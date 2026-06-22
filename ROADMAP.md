# Roadmap

This document describes the near- and medium-term direction for Konflux CI. It reflects current community priorities and is updated through the [governance process](governance.md). The process is currently a manual update of general focus areas, but may be replaced in the future with more tactical tracking of specific scoped and planned features.

---

## Near-Term Focus Areas

### Reliability and Stabilization

The current priority is making Konflux a platform that external communities can adopt and operate with confidence. This means improving transient error resilience across build, integration, and release pipelines; stabilizing multi-platform compute infrastructure; and ensuring pipelines are idempotent and recoverable when things go wrong.

Stability work is paired with observability investment: defining and instrumenting user experience SLOs, adding telemetry to core subsystems, and giving operators dashboards for cluster deployment status and pipeline health. A platform that cannot measure its own reliability cannot improve it.

### Platform Scalability

Konflux scales horizontally by deploying additional independent clusters, but several areas need investment to support larger deployments.

At the per-cluster level, reducing the resource footprint of individual pipeline runs lets each cluster handle more concurrent builds without adding hardware. This means leaner pipeline definitions and moving inline scripts into container images to reduce control plane pressure.

Beyond individual cluster limits, Konflux is working toward multi-cluster pipeline scheduling using Kueue and MultiKueue: a hub cluster can offload pipeline runs to lightweight extension clusters, extending capacity without replicating the full Konflux stack everywhere. This also opens the path to better utilization of heterogeneous compute — pooling specialized build capacity (e.g., alternative architectures) across clusters rather than allocating it statically per cluster.

As deployments grow to multiple clusters, fleet operations become a scaling concern in their own right. Automated provisioning, day-2 operations (upgrades, certificate rotation), and configuration drift detection across a fleet of instances require investment beyond what works for a handful of clusters.

Artifact reuse — building an artifact once and sharing the verified result across pipelines that need it — reduces redundant compute and improves resilience when individual build steps fail on specific architectures. This connects to the artifact-centric provenance work described in the medium-term section: artifacts with their own verifiable attestations are portable by design.

### Dependency Automation and Vulnerability Remediation

The volume of CVEs in modern software outpaces manual triage. Konflux is expanding MintMaker — its automated dependency update system — to respond to vulnerability signals as they emerge rather than on a fixed schedule. Event-driven updates, improved RPM lockfile support, and a CVE scanning gate in the release pipeline will tighten the loop between vulnerability detection and verified remediation.

This work also includes surfacing SAST results back to project teams through the pipeline, and extracting CVE-specific functionality from upstream tooling into the platform itself.

### Community Adoption

Konflux is deployed by organizations running their own instances, installed through the Konflux operator. Near-term work focuses on lowering the barrier to adoption: improving documentation and operational runbooks, reducing the configuration expertise required to stand up a new instance, and smoothing the onboarding experience for communities outside Red Hat. This builds directly on the Fedora SIG's experience as an early external adopter.

A related effort underway in the Konflux community is migrating the API groups in the project's Custom Resource Definitions away from Red Hat-specific naming. This is a prerequisite for genuine vendor neutrality — organizations adopting Konflux should not have Red Hat branding embedded in their Kubernetes API surface.

### Build Platform Breadth

To serve a wider range of open source communities, Konflux is extending its build pipeline support across more language ecosystems and artifact types. Near-term work includes native Gradle build pipelines, support for cloud image pipelines, and initial support for AI model artifacts. For reproducible hermetic builds, Konflux works with the [Hermeto](https://github.com/hermetoproject/hermeto) project; ongoing collaboration focuses on expanding hermetic build support for Java and Maven ecosystems.

Architecture support is also expanding, with RISC-V work underway for relevant release pipelines.

---

## Medium-Term Direction

### Workload Identity and Task-Scoped Attestation

Most CI systems issue a single identity to an entire pipeline, regardless of what each task does. A vulnerability scanner, a build step, and a signing operation all run under the same credential — so a compromised task can make claims it was never authorized to make.

Konflux is working toward task-scoped workload identities using SPIFFE/SPIRE: each task receives an identity tied to its verified task definition, and uses that identity to produce attestations. Policy engines can then evaluate not just whether something was signed, but whether the signer was authorized to make that specific claim. Signature presence alone cannot close this gap.

Related work: OIDC-based keyless signing for build workloads, verifiable SBOM attestation, and integration with the existing Sigstore-based signing infrastructure.

### Artifact-Centric Provenance and Composable Trust

Today, Konflux generates provenance at the PipelineRun level — a single attestation covering the entire pipeline. This works, but it makes individual artifacts hard to verify independently and difficult to reuse across pipelines: the artifact's trustworthiness is bundled with the full pipeline context rather than standing on its own.

The direction is TaskRun-level provenance: each task that produces an OCI artifact generates its own attestation. The final artifact's trust is then established compositionally — as a function of the verified attestations of its dependencies — rather than by re-verifying the entire pipeline. An artifact produced by a trusted scanner task can be consumed by a different pipeline with its trust already established, without requiring the downstream pipeline to repeat the verification.

This shift also simplifies policy evaluation. Rather than reasoning about a monolithic pipeline trace, a policy can evaluate each step's expected inputs, outputs, and attested metadata independently, and verify that the right workload produced the right claim.

Complementary work includes per-task SBOM attestations that aggregate into an accurate build-time SBOM, and runtime instrumentation to auto-generate hermetic build lockfiles — reducing the manual bootstrapping effort for reproducible builds.

Building on task-scoped workload identity, the project is working toward moving scan and test tasks out of the build pipeline and into Integration Test Scenarios — re-runnable independently of the build. Each task generates its own attestation (a vulnerability scan produces a vulnerability attestation; a test produces a test result attestation) signed with the task's workload identity. This decomposes the build pipeline into a graph of independently attested steps, each with a verifiable claim. The design is described in [ADR-0048](https://github.com/konflux-ci/architecture/blob/main/ADR/0048-movable-build-tests.md).

At release time, Conforma evaluates these attestations and can generate a Verification Summary Attestation (VSA) — a high-level summary of the SLSA verification result — or a Software Version Record (SVR), an in-toto attestation predicate that captures the detailed policy evaluation results. Together these make downstream verification tractable: consumers can evaluate a signed summary rather than re-verifying each underlying attestation individually.

### Source Integrity and Policy Enforcement

Supply chain security begins at the source. Konflux integrates with the SLSA source track to verify commit provenance, but enforcing source-level policies — two-person review requirements, branch protection, contributor authorization — requires tooling closer to the repository.

[gittuf](https://gittuf.dev/) stores repository policies as Git references rather than in a separate system, making policy enforcement version-controlled alongside the code and easier to onboard. Adding gittuf (or other source provenance generation) support would let Konflux users establish and verify source-level policies as part of the supply chain, supporting the iterative hardening model where teams ratchet up controls over time.

### Agentic Workload Support

As AI agents generate more code and artifacts, the pipeline must handle provenance, scanning, and attestation for AI-generated content with the same rigor it applies to human-authored code. This includes support for AI model artifact formats, policy-governed promotion systems that account for AI-generated content, and feedback loops between pipeline security results and code-generating agents.

The Secure AI Special Interest Group ([sigs/secure-ai.md](sigs/secure-ai.md)) coordinates work in this area.

### Fedora and Midstream Project Integration

Building on the Fedora SIG's managed cluster, the project will continue expanding support for midstream and community build workflows. This includes improving the experience for projects that build from community sources, and developing patterns that other Linux distribution communities could adopt.

---

## How This Roadmap Is Maintained

Roadmap items reflect areas where active community work is underway or where significant community interest has been expressed. Items are not commitments with fixed delivery dates; they describe direction.

To influence the roadmap, the best paths are:
- Opening GitHub issues on the relevant repository
- Raising topics on the weekly community call
- Participating in the relevant SIG

Large changes to project direction go through the governance committee per [governance.md](governance.md).

# Fedora Konflux Cluster

This is a list of notes about the [Fedora Konflux cluster](https://konflux-ci.fedoraproject.org/).

* **Konflux** is a new build, test, and release platform. Learn more at https://konflux-ci.dev/ and https://github.com/konflux-ci/
* **Fedora** is your Operating System, built with love by people. Learn more at https://fedoraproject.org/

This instance exists to help facilitate a dialog about what the Fedora community wants to do with respect to Konflux. Try to use it to build some stuff and see how the different konflux [resources](https://konflux-ci.dev/architecture/architecture/index.html) work. We'll keep it working and if Fedora decides to use it more, we'll seek a method to support it together with the Fedora Infra team.

Where should we have that dialog? I'm not sure of the best place for now let's try [containers-sig](https://discussion.fedoraproject.org/tags/c/project/7/containers-sig). If you know a better place, let me know and we'll get this pointer updated.

## Important links

* GitHub App (install this first if onboarding a GitHub repo): https://github.com/apps/red-hat-konflux-kflux-fedora-01
* Konflux UI (choose **FAS** authentication to authenticate with FAS): https://konflux-ci.fedoraproject.org
* OpenShift Console: https://console-openshift-console.apps.kflux-fedora-01.84db.p1.openshiftapps.com
* ArgoCD (used for deploying user configurations): https://argocd-tenants-config-server-argocd-tenants-config.apps.kflux-fedora-01.84db.p1.openshiftapps.com

## Onboarding

To onboard to Fedora's Konflux instance, submit a Merge Request to the [tenants-config](https://gitlab.com/fedora/infrastructure/konflux/tenants-config) repository which includes the manifests for creating and configuring your namespace.

See the [tenants-config README](https://gitlab.com/fedora/infrastructure/konflux/tenants-config/-/blob/main/README.md) for detailed instructions on adding a new tenant.

## General Resources

* Upstream user docs (for general usage): https://konflux-ci.dev/docs/
* How to test in Testing Farm from a Konflux integration test scenario: https://konflux-ci.dev/docs/how-tos/testing/integration/third-parties/testing-farm/
* Build-time repo (builds go here as soon as they complete): https://quay.io/organization/konflux-fedora
* Tenant gitops repo (a place where users can put their own namespaces under git control): https://gitlab.com/fedora/infrastructure/konflux/tenants-config

## CLI Access

* Request a token: https://oauth-openshift.apps.kflux-fedora-01.84db.p1.openshiftapps.com/oauth/token/request

```
kubectl login --server=https://api.kflux-fedora-01.84db.p1.openshiftapps.com:6443
```

Using **oc** also works. See also [getting-started/cli/](https://konflux-ci.dev/docs/getting-started/cli/)

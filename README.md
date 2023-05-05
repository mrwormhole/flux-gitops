# Flux GitOps

This repository exists to rule over my k3s clusters. After a long age of years, I finally embraced gitops way of managing my clusters. The thumb of the rule is to never trust any YAMLs on my machine and follow the best gitops practices such as pull based automation for deployments.


This repository bootstrapped via flux(`2.0.0-rc.1`) as follows;

```sh
export GITHUB_TOKEN=<your-token>

flux bootstrap github \
  --owner=my-github-username \
  --repository=my-repository \
  --branch=main \
  --path=clusters/my-cluster \
  --personal
```

Along the way, I have prepared myself to all the problems such as where to store secrets and how to test insecure YAMLs without pushing directly to the repo and waiting for flux. I have solved these problems with bitnami's sealed secrets and fluxCD toolkit.

The folder structure as follows(notice there are no dev/staging/prod because clusters are dealt separately);

```
- /clusters
-- /cluster-name
--- /namespace
---- /app-name
```

Available clusters;

```
- nur-debby
```

**Note: If I had a billion dollar worth, I would pour every penny into flux, It has saved so much pain from my end.**
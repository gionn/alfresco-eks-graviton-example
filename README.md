# Alfresco EKS Graviton example

This is the example code presented during the
[TTL #156 - Towards a sustainable deployment](https://hub.alfresco.com/t5/news-announcements/ttl-156-towards-a-sustainable-deployment/ba-p/318698).

* [acs_values.yml](acs_values.yml): includes values override for the reference deployment without persistency and single replica for most components
* [arm64_selector.yml](arm64_selector.yml) and [amd64_selector.yml](amd64_selector.yml) to target the deployment against a specific `nodeSelector`

Example install with:

```sh
helm upgrade --install acs alfresco/alfresco-content-services --version ~8.0.0
  --namespace alfresco
  --set global.search.sharedSecret=$(openssl rand -hex 24)
  --values acs_values.yml
  --values arm64_selector.yml
```

Reference deployment on an EKS cluster with:

* Graviton (arm64) node group with t4g.xlarge instances
* Classic (amd64) node group with t3a.xlarge instances

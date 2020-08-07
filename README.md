# odh-ml-pipelines

Deploy Minio / Argo / Argo Events
```
kustomize build . /manifest
```

Follow this [readme](manifests/minio/README.md) for creating a bucket named `input` and adding data to it. 

If the workflow doesn't trigger, try restarting the `gateway` pod, and copy the data again (bug).
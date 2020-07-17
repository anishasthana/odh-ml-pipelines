Deploy minio standalone: 

```bash
oc new-project devcon-1
$ cd manifests/minio 
$ kustomize build operator/ | kubectl apply -f -
$ kustomize build server/ | kubectl apply -f -
```

Add MC host: 

```bash
$ mc config host add <ALIAS> <YOUR-S3-ENDPOINT> [YOUR-ACCESS-KEY] [YOUR-SECRET-KEY] [--api API-SIGNATURE]

# Example: 
$ mc config host add devcon-minio http://minio-devcon-1.apps.aasthana.dev.datahub.redhat.com minio minio123 
```

Create a bucket: 
```bash
$ mc mb devcon-minio/test-bucket
$ mc ls devcon-minio
[2020-07-17 13:13:48 EDT]      0B test-bucket/
```

Copy object to bucket: 
```bash
$ touch test-copy.txt
$ mc cp test-copy.txt devcon-minio/test-bucket
```

For more commands see [here](https://docs.min.io/docs/minio-client-quickstart-guide)
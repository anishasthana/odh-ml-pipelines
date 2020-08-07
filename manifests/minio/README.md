Deploy minio standalone: 

```bash
oc new-project devconf
$ cd manifests/minio 
$ kustomize build . | kubectl apply -f -
```

Add MC host: 

```bash
$ mc config host add <ALIAS> <YOUR-S3-ENDPOINT> [YOUR-ACCESS-KEY] [YOUR-SECRET-KEY] [--api API-SIGNATURE]

# Example: 
$ mc config host add devconf http://minio-devconf.apps.hukhan.dev.datahub.redhat.com minio minio123 
```

Create a bucket: 
```bash
$ mc mb devconf/input
$ mc ls devconf
[2020-07-17 13:13:48 EDT]      0B input/
```

Copy object to bucket: 
```bash
$ touch test-copy.txt
$ mc cp test-copy.txt devconf/input
```

For more commands see [here](https://docs.min.io/docs/minio-client-quickstart-guide)
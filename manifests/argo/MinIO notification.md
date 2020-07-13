# Consumed notifications

## Overall Argo Events event structure

> Taken from [Argo Events docs](https://argoproj.github.io/argo-events/setup/minio/#event-structure)

```json
{
  "context": {
    "type": "type_of_gateway",
    "specVersion": "cloud_events_version",
    "source": "name_of_the_gateway",
    "eventID": "unique_event_id",
    "time": "event_time",
    "dataContentType": "type_of_data",
    "subject": "name_of_the_event_within_event_source"
  },
  "data": {
    "notification": [
      //   List of MinIO notifications
    ]
  }
}
```

## Example of a MinIO notification

> Taken from [MinIO docs](https://github.com/minio/minio/blob/master/docs/bucket/notifications/README.md#step-4-test-on-kafka)

```json
{
  "eventVersion": "2.0",
  "eventSource": "minio:s3",
  "awsRegion": "",
  "eventTime": "2019-09-10T17:41:54Z",
  "eventName": "s3:ObjectCreated:Put",
  "userIdentity": {
    "principalId": "AKIAIOSFODNN7EXAMPLE"
  },
  "requestParameters": {
    "accessKey": "AKIAIOSFODNN7EXAMPLE",
    "region": "",
    "sourceIPAddress": "192.168.56.192"
  },
  "responseElements": {
    "x-amz-request-id": "15C3249451E12784",
    "x-minio-deployment-id": "751a8ba6-acb2-42f6-a297-4cdf1cf1fa4f",
    "x-minio-origin-endpoint": "http://192.168.97.83:9000"
  },
  "s3": {
    "s3SchemaVersion": "1.0",
    "configurationId": "Config",
    "bucket": {
      "name": "images",
      "ownerIdentity": {
        "principalId": "AKIAIOSFODNN7EXAMPLE"
      },
      "arn": "arn:aws:s3:::images"
    },
    "object": {
      "key": "myphoto.jpg",
      "size": 6474,
      "eTag": "430f89010c77aa34fc8760696da62d08-1",
      "contentType": "image/jpeg",
      "userMetadata": {
        "content-type": "image/jpeg"
      },
      "versionId": "1",
      "sequencer": "15C32494527B46C5"
    }
  },
  "source": {
    "host": "192.168.56.192",
    "port": "",
    "userAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:69.0) Gecko/20100101 Firefox/69.0"
  }
}
```

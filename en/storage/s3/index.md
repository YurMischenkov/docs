# How to use the API

## Before you start {#preparations}

To use the API:

{% include [storage-s3-http-api-preps](../_includes_service/storage-s3-http-api-preps.md) %}

To access the HTTP API directly, you need static key authentication, which is supported by the tools listed in [{#T}](../instruments/index.md).

For a list of supported Amazon S3 HTTP API methods, see the [API reference](api-ref/index.md).

## General API request format {#common-request-form}

```
{GET|HEAD|PUT|DELETE} /<bucket>/<key> HTTP/1.1
Host: storage.yandexcloud.net
Content-Length: length
Date: date
Authorization: authorization string (AWS Signature Version 4)

Request_body
```

The name of the bucket can be specified as part of the host name. In this case, the request looks like:

```
{GET|HEAD|PUT|DELETE} /<key>} HTTP/1.1
Host: <bucket>.storage.yandexcloud.net
...
```

The set of headers depends on the specific request and is described in the documentation for the corresponding request.

If you use the API directly (without an SDK or apps), you need to generate the `Authorization` header yourself for authenticating requests. Find out how to do this in the Amazon S3 documentation: [Authenticating Requests (AWS Signature Version 4)](https://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-authenticating-requests.html).

### Request URL {#request-url}

URLs can taken one of the following forms:

- `https://{{ s3-storage-host }}/<bucket>/<key>?<parameters>`
- `https://<bucket>.{{ s3-storage-host }}/<key>?<parameters>`

## CORS requests

Cross-domain requests are available for all API methods used for object management.

To check permissions, CORS sends the [options](api-ref/object/options.md) preflight request to a resource. {{ objstorage-name }} allows you to skip the preflight request when sending cross-domain requests to resources. In this case, your request [headers](api-ref/object/options.md#request-headers) must be the same as those in the preflight request.


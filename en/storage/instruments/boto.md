# boto3 and boto

[The boto3](https://github.com/boto/boto3) and [boto](https://github.com/boto/boto) development tools offer SDKs for the Python 2.x and 3.x programming languages. The SDKs are designed for working with AWS services.

## Before you start {#preparations}

{% include [storage-s3-http-api-preps](../_includes_service/storage-s3-http-api-preps.md) %}

## Installation {#installation}

To install boto, use the instructions in the developer's repository: [boto3](https://github.com/boto/boto3/blob/develop/README.rst#quick-start), [boto](https://github.com/boto/boto#installation).

## Configuration {#setup}

{% include [storage-sdk-setup](../_includes_service/storage-sdk-setup.md) %}

## Example {#boto-example}

{% list tabs %}

- boto3

  ```python
  #!/usr/bin/env python
  #-*- coding: utf-8 -*-
  import boto3
  session = boto3.session.Session()
  s3 = session.client(
      service_name='s3',
      endpoint_url='https://storage.yandexcloud.net'
  )
  
  # Create a new bucket
  s3.create_bucket(Bucket='bucket-name')
  
  # Uploading objects into the bucket
  
  ## From a string
  s3.put_object(Bucket='bucket-name', Key='object_name', Body='TEST', StorageClass='COLD')
  
  ## From a file
  s3.upload_file('this_script.py', 'bucket-name', 'py_script.py')
  s3.upload_file('this_script.py', 'bucket-name', 'script/py_script.py')
  
  # Getting a list of objects in the bucket
  for key in s3.list_objects(Bucket='bucket-name')['Contents']:
      print(key['Key'])
  
  # Deleting multiple objects
  forDeletion = [{'Key':'object_name'}, {'Key':'script/py_script.py'}]
  response = s3.delete_objects(Bucket='bucket-name', Delete={'Objects': forDeletion})
  
  # Retrieve an object
  get_object_response = s3.get_object(Bucket='bucket-name',Key='py_script.py')
  print(get_object_response['Body'].read())
  ```

- boto

  ```python
  #!/usr/bin/env python
  #-*- coding: utf-8 -*-
  import os
  from boto.s3.key import Key
  from boto.s3.connection import S3Connection
  os.environ['S3_USE_SIGV4'] = 'True'
  conn = S3Connection(
      host='storage.api.cloud.yandex.net'
  )
  conn.auth_region_name = 'ru-central1'
  
  # Create a new bucket
  conn.create_bucket('bucket-name')
  bucket = conn.get_bucket('bucket-name')
  
  # Uploading objects into the bucket
  
  ## From a string
  bucket.new_key('test-string').set_contents_from_string('TEST')
  
  ## From a file
  file_key_1 = Key(bucket)
  file_key_1.key = 'py_script.py'
  file_key_1.set_contents_from_filename('this_script.py')
  file_key_2 = Key(bucket)
  file_key_2.key = 'script/py_script.py'
  file_key_2.set_contents_from_filename('this_script.py')
  
  # Getting a list of objects in the bucket
  keys_list=bucket.list()
  for key in keys_list:
      print key.key
  
  # Deleting multiple objects
  response = bucket.delete_keys(['test-string', 'py_script.py'])
  
  # Retrieve an object
  key = bucket.get_key('script/py_script.py')
  print key.get_contents_as_string()
  ```

{% endlist %}


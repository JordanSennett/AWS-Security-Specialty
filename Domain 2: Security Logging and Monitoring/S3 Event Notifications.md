# S3 Event Notifications

- S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication
- Object name filtering possible (*.jpg)
- Use case: generate thumbnails of images uploaded to S3
- Can create as many “S3 events” as desired
- S3 event notifications typically deliver events in seconds but can sometimes take a minute or longer
![S3 notification flow](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/25cc39cc-da48-4e01-9b95-b71978ad0c1c)


**S3 Event Notifications – IAM Permissions**

![S3 IAM permissions per alerting process](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/0da3b8a1-1590-40c4-8597-649448dff54f)

**S3 Event Notifications with Amazon EventBridge**

- Advanced filtering options with JSON rules (metadata, object size, name...)
- Multiple Destinations – ex Step Functions, Kinesis Streams / Firehose...
- EventBridge Capabilities – Archive, Replay Events, Reliable delivery

![S3 notifications using EventBridge](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/f8bf5723-54b6-499a-8b4e-08621b0c4138)

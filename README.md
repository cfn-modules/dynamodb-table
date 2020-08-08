# cfn-modules: AWS DynamoDB table

AWS DynamoDB table with auto scaling and [alerting](https://www.npmjs.com/package/@cfn-modules/alerting).

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/dynamodb-table
```

## Usage

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Table:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        AlertingModule: !GetAtt 'Alerting.Outputs.StackName' # optional
        KmsKeyModule: !GetAtt 'Key.Outputs.StackName' # optional
        TableName: user # optional
        PartitionKeyName: id # optional
        PartitionKeyType: S # optional
        SortKeyName: '' # optional
        SortKeyType: N # optional
        BillingAndScalingMode: PROVISIONED # optional
        MaxWriteCapacityUnits: '1' # optional
        MinWriteCapacityUnits: '1' # optional
        WriteCapacityUnitsUtilizationTarget: '80' # optional
        MaxReadCapacityUnits: '1' # optional
        MinReadCapacityUnits: '1' # optional
        ReadCapacityUnitsUtilizationTarget: '80' # optional
        Encryption: 'false' # optional; deprecated in v1, will be removed in v3, use KmsKeyModule instead!
        StreamViewType: DISABLED # optional
        TtlAttributeName: '' # optional
        BackupRetentionPeriod: '30' # optional
        BackupScheduleExpression: 'cron(0 5 ? * * *)' # optional
        PointInTimeRecoveryEnabled: 'true' # optional
      TemplateURL: './node_modules/@cfn-modules/dynamodb-table/module.yml'
```

## Examples

* [serverless-iam](https://github.com/cfn-modules/docs/tree/master/examples/serverless-iam)

## Related modules

* [lambda-event-source-dynamodb-stream](https://github.com/cfn-modules/lambda-event-source-dynamodb-stream)

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>AlertingModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/alerting">alerting module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
     <tr>
      <td>KmsKeyModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/kms-key">kms-key module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>TableName</td>
      <td>Name of the table</td>
      <td>auto generated value</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>PartitionKeyName</td>
      <td>Name of the partition key</td>
      <td>id</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>PartitionKeyType</td>
      <td>Type of the partition key</td>
      <td>S</td>
      <td>no</td>
      <td>[S, N, B]</td>
    </tr>
    <tr>
      <td>SortKeyName</td>
      <td>Name of the sort key</td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>SortKeyType</td>
      <td>Type of the sort key (if SortKeyName is set)</td>
      <td>N</td>
      <td>no</td>
      <td>[S, N, B]</td>
    </tr>
    <tr>
      <td>BillingAndScalingMode</td>
      <td>Specify how you are charged for read and write throughput and how you manage capacity.</td>
      <td>PROVISIONED</td>
      <td>no</td>
      <td>[PROVISIONED, ONDEMAND]</td>
    </tr>
    <tr>
      <td>MaxWriteCapacityUnits</td>
      <td>Maximum write capacity units used during auto scaling</td>
      <td>1</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>MinWriteCapacityUnits</td>
      <td>Minimum write capacity units used during auto scaling</td>
      <td>1</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>WriteCapacityUnitsUtilizationTarget</td>
      <td>Target write capacity utilization (in percent) that auto scaling tries to achieve (if you have spiky writes, a lower number is better)</td>
      <td>80</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>MaxReadCapacityUnits</td>
      <td>Maximum read capacity units used during auto scaling</td>
      <td>1</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>MinReadCapacityUnits</td>
      <td>Minimum read capacity units used during auto scaling</td>
      <td>1</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>ReadCapacityUnitsUtilizationTarget</td>
      <td>Target read capacity utilization (in percent) that auto scaling tries to achieve (if you have spiky reads, a lower number is better)</td>
      <td>80</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>Encryption</td>
      <td>Deprecated in v1, will be removed in v3, use KmsKeyModule instead! Enable server side encryption using KMS (AWS managed) CMK</td>
      <td>false</td>
      <td>no</td>
      <td>[aws, false]</td>
    </tr>
    <tr>
      <td>StreamViewType</td>
      <td>Determines the information that the stream captures when an item in the table is modified</td>
      <td>DISABLED</td>
      <td>no</td>
      <td>[DISABLED, KEYS_ONLY, NEW_IMAGE, OLD_IMAGE, NEW_AND_OLD_IMAGES]</td>
    </tr>
    <tr>
      <td>TtlAttributeName</td>
      <td>Name of the TTL attribute that stores the expiration time for items in the table. The name can be 1–255 characters long, and has no character restrictions. (TTL is disabled if not set)</td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>BackupRetentionPeriod</td>
      <td>The number of days to keep backups of the table (set to 0 to disable)</td>
      <td>30</td>
      <td>no</td>
      <td>[0-35]</td>
    </tr>
    <tr>
      <td>BackupScheduleExpression</td>
      <td>A CRON expression specifying when AWS Backup initiates a backup job</td>
      <td>cron(0 5 ? * * *)</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>PointInTimeRecoveryEnabled</td>
      <td>Indicates whether point in time recovery is enabled (true) or disabled (false) on the table</td>
      <td>true</td>
      <td>no</td>
      <td>[true, false]</td>
    </tr>
  </tbody>
</table>

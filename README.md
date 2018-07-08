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
        TableName: user # optional
        PartitionKeyName: id # optional
        PartitionKeyType: S # optional
        SortKeyName: '' # optional
        SortKeyType: N # optional
        MaxWriteCapacityUnits: 1 # optional
        MinWriteCapacityUnits: 1 # optional
        WriteCapacityUnitsUtilizationTarget: 80 # optional
        MaxReadCapacityUnits: 1 # optional
        MinReadCapacityUnits: 1 # optional
        ReadCapacityUnitsUtilizationTarget: 80 # optional
        Encryption: false # optional
      TemplateURL: './node_modules/@cfn-modules/dynamodb-table/module.yml'
```

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
      <td>Enable server side encryption using KMS (AWS managed) CMK</td>
      <td>false</td>
      <td>no</td>
      <td>[aws, false]</td>
    </tr>
  </tbody>
</table>

## Limitations

* Secure: DynamoDB table is not backed up


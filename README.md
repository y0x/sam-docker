# SAM-Docker

This repository allows to easily setup a local dynamoDB that is preconfigured to be easily used with AWS-SAM for local testing.

Currently supported services by this repository:

- DynamoDB

## Docker usage

Start linked services:

`docker-compose up`

Stop services:

`docker-compose down`

## Table usage

create-table.json contains basic table structure and can be adjusted to your needs. Create a table by executing:

`aws dynamodb create-table --cli-input-json file://json/create-table.json --endpoint-url http://localhost:8000`

Verify if table exist:

`aws dynamodb list-tables --endpoint-url http://localhost:8000`

put-item.json can be used to put an item to the table:

`aws dynamodb put-item --table-name ExampleTable --item file://json/put-item.json --return-consumed-capacity TOTAL --endpoint-url http://localhost:8000`

Scan Table

`aws dynamodb scan --table-name ExampleTable --endpoint-url http://localhost:8000`

Delete Table

`aws dynamodb delete-table --table-name ExampleTable --endpoint-url http://localhost:8000`

## AWS SAM usage

Following steps require basic sam infrastructure. Can be created with `sam init`.

Start local api

`sam local start-api --env-vars json/env.json`

Create your DynamoDBClient with the following configuration

```
region: 'eu-central-1' #Must match the value from json/env.json
endpoint: 'http://dynamo:8000'
```

As TableName use the value from json/env.json (This must match the value from json/create-table.json)

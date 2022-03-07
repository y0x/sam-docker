# SAM-Docker

This repository allows to easily setup a local dynamoDB that is preconfigured to be easily used with AWS-SAM for local testing.

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

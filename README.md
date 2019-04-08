# multiple-cloudwatch-logs-streamed-to-elasticsearch
This lambda function is slightly different than the default LogsToElasticsearch created by AWS when you attempt to stream to Elasticsearch. This allows for the use of multiple log groups. With the AWS provided example multiple log groups are not allowed due to index restrictions in elasticsearch 6.0

# multiple-cloudwatch-logs-streamed-to-elasticsearch

### About
This lambda function is to replace the default lambda that is created when you stream CloudWatch Logs -> Elasticsearch. This lambda function allows the use of multiple CloudWatch Log Groups to the streaming of one Elasticsearch cluster.

### Primary Change & Reasoning
The only code difference between this lambda function and the default lambda function is the variable indexName:

```
        var indexName = [
            'cwl-' + payload.logGroup.toLowerCase().split('/').join('-') + '-' + timestamp.getUTCFullYear(),              // log group + year
            ('0' + (timestamp.getUTCMonth() + 1)).slice(-2),  // month
            ('0' + timestamp.getUTCDate()).slice(-2)          // day
        ].join('.');
```

This is required due to a change in Elasticsearch 6.0 that allows indicies to only containe a single mapping type. 

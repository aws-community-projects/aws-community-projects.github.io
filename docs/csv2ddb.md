# Csv2Ddb

Lambda function fetches a 100 line csv file from S3 and saves it line-by-line to DynamoDB. Uses 3rd party [csvtojson lib](https://github.com/Keyang/node-csvtojson). [source](https://github.com/aws-community-projects/community-benchmarks/tree/main/stacks/test-stacks). 

Test run is 20 executions with 10 concurrency (50% cold start) using nodejs14.x, arm64 and 512 memory.

| Name                        | Description                          | p50 Duration | p90 Duration | p50 Cold Start | p90 Cold Start | CodeSize |
| --------------------------- | ------------------------------------ | ------------ | ------------ | -------------- | -------------- | -------- |
| csv2ddb-sdk3                | sdkv3 w/esm                          | 1416.4       | 2331.89      | 733.27         | 763.06         | 782229   |
| csv2ddb-sdk2-native         | native sdkv2                         | 1163.48      | 1591.81      | 620.69         | 625.14         | 132402   |
| csv2ddb-sdk2-mjs            | esm, sdkv2, no transpiling           | 2279.59      | 3252.52      | 666.89         | 683.97         | 2478799  |
| csv2ddb-sdk2-layer          | aws-sdkv2 in a Lambda Layer          | 1128.45      | 1697.42      | 749.73         | 764.68         | 132402   |
| csv2ddb-sdk2-js             | commonjs, sdkv2, no transpiling      | 2220.92      | 2679.97      | 650.55         | 672.76         | 2478584  |
| csv2ddb-sdk2-esm            | full sdkv2, bundled with esm         | 1115.89      | 1310.63      | 1220.07        | 1236.26        | 2395978  |
| csv2ddb-sdk2-clients-native | clients only, native sdkv2           | 1172.29      | 1859.28      | 421.93         | 428.93         | 132465   |
| csv2ddb-sdk2-clients-esm    | clients only sdkv2, bundled with esm | 1182.05      | 1904.7       | 566.3          | 585.6          | 634057   |

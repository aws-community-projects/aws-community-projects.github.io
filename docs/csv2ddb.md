# Csv2Ddb

Lambda function fetches a 100 line csv file from S3 and saves it line-by-line to DynamoDB. Uses 3rd party [csvtojson lib](https://github.com/Keyang/node-csvtojson). [source](https://github.com/aws-community-projects/community-benchmarks/tree/main/stacks/test-stacks). 

Test run is 20 executions with 10 concurrency (50% cold start) using nodejs14.x, arm64 and 512 memory.

| Name                             | Description                       | p50 Duration | p90 Duration | p50 Cold Start | p90 Cold Start | CodeSize |
| -------------------------------- | --------------------------------- | ------------ | ------------ | -------------- | -------------- | -------- |
| csv2ddb-sdk2-clients-ts          | clients only, sdkv2, ts           | 355.95       | 419.38       | 558.33         | 567.84         | 544485   |
| csv2ddb-sdk2-clients-ts-xray     | clients only, sdkv2, ts, xray     | 1059.86      | 1333.88      | 598.27         | 616.46         | 662696   |
| csv2ddb-sdk2-clients-native      | clients only, sdkv2, native       | 362.46       | 453.07       | 559.02         | 575.49         | 544485   |
| csv2ddb-sdk2-clients-native-xray | clients only, sdkv2, native, xray | 1075.45      | 1326.4       | 601.81         | 624.33         | 662696   |
| csv2ddb-sdk2-esm                 | full sdkv2, ts                    | 296.19       | 417.78       | 1035.35        | 1107           | 1615129  |
| csv2ddb-sdk2-js                  | full sdkv2, cjs                   | 361.92       | 440.38       | 667.8          | 683.95         | 2478715  |
| csv2ddb-sdk2-js-xray             | full sdkv2, cjs, xray             | 390.92       | 489.23       | 702.71         | 735.73         | 3160739  |
| csv2ddb-sdk2-layer               | full sdkv2 in layer, ts           | 307.73       | 473.68       | 1037.79        | 1114.96        | 1615129  |
| csv2ddb-sdk2-mjs                 | sdkv2, mjs                        | 377.3        | 452.43       | 670.9          | 704.93         | 2478959  |
| csv2ddb-sdk2-mjs-xray            | sdkv2, mjs, xray                  | 417.26       | 540.82       | 721.52         | 751.65         | 3160978  |
| csv2ddb-sdk2-native              | native sdkv2, ts                  | 336.24       | 444.01       | 989.28         | 1105.62        | 1615129  |
| csv2ddb-sdk3                     | sdkv3, ts                         | 223.18       | 416.75       | 716.55         | 727.53         | 665087   |
| csv2ddb-sdk3-mjs                 | sdkv3, mjs                        | 127.13       | 323.48       | 1065.73        | 1097.85        | 6184720  |
| csv2ddb-sdk3-mjs-xray            | sdkv3, mjs, xray                  | 316.95       | 585.63       | 1113.81        | 1135.44        | 6799626  |
| csv2ddb-sdk3-xray                | sdkv3, ts, xray                   | 303.62       | 439.05       | 754.71         | 799.35         | 782505   |

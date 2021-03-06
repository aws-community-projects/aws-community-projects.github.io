# Csv2Ddb

Lambda function fetches a 100 line csv file from S3 and saves it line-by-line to DynamoDB. Uses 3rd party [csvtojson lib](https://github.com/Keyang/node-csvtojson). [source](https://github.com/aws-community-projects/community-benchmarks/tree/main/stacks/test-stacks). 

Test run is 50 executions with 10 concurrency (20% cold start).

| architectures | averageColdStart | averageDuration | codeSize | coldStartPercent | date       | format | iterations | memorySize | minify | p90ColdStart | p90Duration | runtime    | sdk          | sourceType | xray  |
| ------------- | ---------------- | --------------- | -------- | ---------------- | ---------- | ------ | ---------- | ---------- | ------ | ------------ | ----------- | ---------- | ------------ | ---------- | ----- |
| arm64         | 826.74           | 145.34          | 749818   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 835.39       | 335.13      | nodejs14.x | sdk3         | ts         | false |
| arm64         | 501.74           | 734.66          | 252014   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 537.23       | 1260.65     | nodejs14.x | sdk2-clients | ts         | true  |
| arm64         | 1074.54          | 143.27          | 3945101  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1116.82      | 478.44      | nodejs16.x | sdk3-modules | ts         | false |
| arm64         | 565.77           | 587.96          | 663246   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 592.38       | 1229.4      | nodejs16.x | sdk2-clients | ts         | true  |
| arm64         | 510.39           | 144.96          | 545069   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 522.71       | 565.64      | nodejs16.x | sdk2-clients | ts         | false |
| arm64         | 637.55           | 117.17          | 665089   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 650.74       | 367.1       | nodejs16.x | sdk3         | ts         | false |
| arm64         | 1060.96          | 116.96          | 6182876  | 20               | 2022-05-10 | esm    | 50         | 512        | false  | 1101.45      | 295.72      | nodejs16.x | sdk3-modules | mjs        | false |
| arm64         | 1133.53          | 158.94          | 1624408  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1165.49      | 398.75      | nodejs16.x | sdk2         | ts         | false |
| arm64         | 1132.68          | 150.4           | 6797438  | 20               | 2022-05-10 | esm    | 50         | 512        | false  | 1152.56      | 388.41      | nodejs14.x | sdk3-modules | mjs        | true  |
| arm64         | 765.67           | 180.12          | 867015   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 774.86       | 439.02      | nodejs16.x | sdk3         | ts         | true  |
| arm64         | 583.95           | 190.04          | 545069   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 607.18       | 400.22      | nodejs14.x | sdk2-clients | ts         | false |
| arm64         | 1060.04          | 118.43          | 6182876  | 20               | 2022-05-10 | esm    | 50         | 512        | false  | 1070.61      | 313.09      | nodejs14.x | sdk3-modules | mjs        | false |
| arm64         | 474.22           | 632.47          | 252014   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 506.71       | 1260.91     | nodejs16.x | sdk2-clients | ts         | true  |
| arm64         | 670.41           | 180.3           | 132891   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 779.37       | 396.2       | nodejs14.x | sdk2         | ts         | false |
| arm64         | 1039.24          | 138.59          | 3945101  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1070.68      | 345.5       | nodejs14.x | sdk3-modules | ts         | false |
| arm64         | 686.69           | 632.84          | 251972   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 733.31       | 1317.04     | nodejs16.x | sdk2         | ts         | true  |
| arm64         | 813.1            | 132.83          | 3945482  | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 836.44       | 348.99      | nodejs16.x | sdk3-modules | ts         | false |
| arm64         | 617.65           | 693.37          | 663246   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 636.24       | 1210.95     | nodejs14.x | sdk2-clients | ts         | true  |
| arm64         | 1031.09          | 188.03          | 1624408  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1158.75      | 439.46      | nodejs14.x | sdk2         | ts         | false |
| arm64         | 854.23           | 173.88          | 867015   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 870.23       | 418.54      | nodejs14.x | sdk3         | ts         | true  |
| arm64         | 1026.83          | 970.56          | 1743248  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1064.79      | 1344.2      | nodejs14.x | sdk2         | ts         | true  |
| arm64         | 829.28           | 158.3           | 3956871  | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 862.32       | 402.1       | nodejs16.x | sdk3-modules | ts         | true  |
| arm64         | 724.23           | 124.78          | 665089   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 756.63       | 309.73      | nodejs14.x | sdk3         | ts         | false |
| arm64         | 448.84           | 197.99          | 132954   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 474          | 476.49      | nodejs14.x | sdk2-clients | ts         | false |
| arm64         | 844.31           | 140.78          | 3945567  | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 854.19       | 359.31      | nodejs14.x | sdk3-modules | ts         | true  |
| arm64         | 735.42           | 150.77          | 749818   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 773.41       | 399.34      | nodejs16.x | sdk3         | ts         | false |
| arm64         | 1138.85          | 148.81          | 6797438  | 20               | 2022-05-10 | esm    | 50         | 512        | false  | 1149.54      | 493.54      | nodejs16.x | sdk3-modules | mjs        | true  |
| arm64         | 1072.38          | 151.4           | 3945169  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1091.69      | 523.05      | nodejs16.x | sdk3-modules | ts         | true  |
| arm64         | 1053.73          | 167.89          | 3945169  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1089.85      | 393.04      | nodejs14.x | sdk3-modules | ts         | true  |
| arm64         | 644.59           | 179.24          | 132891   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 687.96       | 559.44      | nodejs16.x | sdk2         | ts         | false |
| arm64         | 705.13           | 688.05          | 251972   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 754.7        | 1218.75     | nodejs14.x | sdk2         | ts         | true  |
| arm64         | 1039.23          | 914.12          | 1743248  | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 1054.86      | 1282.42     | nodejs16.x | sdk2         | ts         | true  |
| arm64         | 764.21           | 162.38          | 782455   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 786.86       | 394.02      | nodejs14.x | sdk3         | ts         | true  |
| arm64         | 848.4            | 131.39          | 3945482  | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 869.21       | 318.33      | nodejs14.x | sdk3-modules | ts         | false |
| arm64         | 734.72           | 199.22          | 782455   | 20               | 2022-05-10 | esm    | 50         | 512        | true   | 755.49       | 393.6       | nodejs16.x | sdk3         | ts         | true  |
| arm64         | 441.76           | 183.69          | 132954   | 20               | 2022-05-10 | cjs    | 50         | 512        | true   | 466.97       | 464.85      | nodejs16.x | sdk2-clients | ts         | false |


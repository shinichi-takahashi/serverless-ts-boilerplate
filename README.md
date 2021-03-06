# serverless-ts-boilerplate

Example project built with [TypeScript](https://www.typescriptlang.org/), [Serverless Framework](https://serverless.com/framework/), [Webpack](https://webpack.github.io/), [TSLint](https://palantir.github.io/tslint/) and [Source Map Support](https://github.com/evanw/node-source-map-support).

## Usage

Clone the repo.

```
$ git clone git@github.com/y13i/serverless-ts-boilerplate.git
```

Install dependencies.

```
$ cd serverless-ts-boilerplate
$ yarn
```

Replace service name in `serverless.yml`

```
$ sed -i -e 's/serverless-ts-boilerplate/my-service/g' serverless.yml
```

Deploy example.

```
$ yarn run deploy
```

Try HTTP request.

```
$ curl -s "https://${API_ID}.execute-api.${AWS_REGION}.amazonaws.com/dev/hello" | jq
```

With some parameters.

```
$ curl -s "https://${API_ID}.execute-api.${AWS_REGION}.amazonaws.com/dev/hello?name=Donald&yourName=Hillary" | jq
```

Raise some error.

```
$ curl -s "https://${API_ID}.execute-api.${AWS_REGION}.amazonaws.com/dev/hello?yourName=Voldemort" | jq
```

Confirm sourcemap works.

```
$ node_modules/.bin/serverless invoke --function hello --data '{"queryStringParameters": {"yourName": "Voldemort"}}'
```

You can also review errors in CloudWatch Logs by using `serverless logs` command.

```
$ yarn run serverless -- logs --function hello
```

Remove resources.

```
$ yarn run remove
```

Happy coding!

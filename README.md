
# Go lambda with DynamoDB

> [!TIP]
> To deploy this project using **GUI-based flow**, navigate to [console](https://console.stacktape.com/create-new-project/git-project-using-console?name=my-stacktape-app&repositoryType=public&repositoryUrl=https://github.com/stacktape/starter-go-lambda-api)

- simple Lambda-based HTTP API using Go runtime.
- The application runs in a [Lambda function](https://docs.stacktape.com/resources/lambda-functions/) and uses
  [DynamoDb](https://docs.stacktape.com/resources/dynamo-db-tables/) to store the data.
- This project includes a pre-configured [stacktape.yml configuration](stacktape.yml).
The configured infrastructure is described in the [stack description section](#stack-description)

## Pricing


- The infrastructure required for this application uses exclusively "serverless", pay-per-use infrastructure. If your load won't get high, these costs will be close to $0.

## Prerequisites

1. **AWS account**. If you don't have one, [create new account here](https://portal.aws.amazon.com/billing/signup).

2. **Stacktape account**. If you don't have one, [create new account here](https://console.stacktape.com/sign-up).

3. **Stacktape installed**.

  <details>
  <summary>Install on Windows (Powershell)</summary>

  ```bash
  iwr https://installs.stacktape.com/windows.ps1 -useb | iex
  ```

  </details>
  <details>
  <summary>Install on Linux</summary>

  ```bash
  curl -L https://installs.stacktape.com/linux.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS ARM (Apple silicon)</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos-arm.sh | sh
  ```

  </details>




## 1. Generate your project
To initialize the project, use

```bash
stacktape init --starterId go-lambda-api
```




## 2. Deploy your stack

The deployment will take ~5-15 minutes. Subsequent deploys will be significantly faster.

<details>
<summary>Deploy from local machine</summary>

<br />

The deployment from local machine will build and deploy the application from your system. This means you also need to have:
- Docker. To install Docker on your system, you can follow [this guide](https://docs.docker.com/get-docker/).

<br />

To perform the deployment, use the following command:

```bash
stacktape deploy --projectName <<project-name>> --stage <<stage>> --region <<region>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using AWS CodeBuild pipeline</summary>

<br />

Deployment using AWS CodeBuild will build and deploy your application inside [AWS CodeBuild pipeline](https://aws.amazon.com/codebuild/). To perform the deployment, use

```bash
stacktape codebuild:deploy --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Github actions CI/CD pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://github.com/new
2. Create Github repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-github-repository-secrets
3. Replace `<<stage>>` and `<<region>>` in the .github/workflows/deploy.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@github.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. To monitor the deployment progress, navigate to your github project and select the Actions tab

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Gitlab CI pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://gitlab.com/projects/new
2. Create Gitlab repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-gitlab-repository-secrets
3. replace `<<stage>>` and `<<region>>` in the .gitlab-ci.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@gitlab.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. `To monitor the deployment progress, navigate to your gitlab project and select CI/CD->jobs`

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>

## 3. Test your application

After a successful deployment, some information about the stack will be printed to the terminal (**URLs** of the deployed services, links to **logs**, **metrics**, etc.).

To test the application, you will need the web service URL. It's printed to the terminal.

### Create a post
Make a `POST` request to `<<web_service_url>>/post` with the JSON data in its body to save the post. Use your preferred HTTP client or
the following cURL command:

```bash
curl -X POST <<web_service_url>>/posts -H 'content-type: application/json' -d '{ "title": "MyPost", "content": "Hello!", "authorEmail": "info@stacktape.com"}'
```

If the above cURL command did not work, try escaping the JSON content:

```bash
curl -X POST <<web_service_url>>/posts -H 'content-type: application/json' -d '{ \"title\":\"MyPost\",\"content\":\"Hello!\",\"authorEmail\":\"info@stacktape.com\"}'
```

### Get all posts

Make a `GET` request to `<<web_service_url>>/posts` to get all posts.

```bash
curl <<web_service_url>>/posts
```

## 4. Run the application in development mode
To run functions in the development mode (remotely on AWS), you can use the
[dev command](https://docs.stacktape.com/cli/commands/dev/). For example, to develop and debug lambda function `savePost`, you can use

```bash
stacktape dev --region <<your-region>> --stage <<stage>> --resourceName savePost
```

The command will:
- quickly re-build and re-deploy your new function code
- watch for the function logs and pretty-print them to the terminal

The function is rebuilt and redeployed, when you either:
- type `rs + enter` to the terminal
- use the `--watch` option and one of your source code files changes

## 5. Hotswap deploys
- Stacktape deployments use [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) under the hood. It
  brings a lot of guarantees and convenience, but can be slow for certain use-cases.

- To speed up the deployment, you can use the `--hotSwap` flag which avoids using Cloudformation.
- Hotswap deployments work only for source code changes (for lambda function, containers and batch jobs) and for content uploads to buckets.
- If the update deployment is not hot-swappable, Stacktape will automatically fall back to using a Cloudformation deployment.
```bash
stacktape deploy --hotSwap --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

## 6. Delete your stack

- If you no longer want to use your stack, you can delete it.
- Stacktape will automatically delete every infrastructure resource and deployment artifact associated with your stack.

```bash
stacktape delete --stage <<stage>> --region <<region>>
```

# Stack description

  Stacktape uses a simple `stacktape.yml` configuration file to describe infrastructure resources, packaging, deployment
  pipeline and other aspects of your project.

  You can deploy your project to multiple environments (stages) - for
  example `production`, `staging` or `dev-john`. A stack is a running instance of an project. It consists of your application
  code (if any) and the infrastructure resources required to run it.

  The configuration for this project is described below.

  ## 1. Resources

  - Every resource must have an arbitrary, alphanumeric name (A-z0-9).
  - Stacktape resources consist of multiple underlying AWS or 3rd party resources.
### 1.1 HTTP API Gateway

API Gateway receives requests and routes them to the container.

For convenience, it has [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) allowed.

```yml
resources:
  mainApiGateway:
    type: http-api-gateway
    properties:
      cors:
        enabled: true
```

### 1.2 DynamoDB table

The application data is stored in a DynamoDB table.

Only the primary key of the table needs to be configured in a minimal setup. You can also configure
[other properties](https://docs.stacktape.com/resources/dynamo-db-tables/) if desired.

```yml
mainDynamoDbTable:
  type: dynamo-db-table
  properties:
    primaryKey:
      partitionKey:
        name: id
        type: string
```

### 1.3 Functions

The core of our application consists of two serverless functions:

- **savePost function** - saves post into database(DynamoDB)
- **getPosts function** - get all posts from the database(DynamoDB)

Functions are configured as follows:

- **Packaging** - determines how the lambda artifact is built. The easiest and most optimized way to build the lambda is
  using `stacktape-lambda-buildpack`. We only need to configure `entryfilePath`. Stacktape automatically builds the
  application code with all of its dependencies, creates the lambda zip artifact, and uploads it to a pre-created S3
  bucket on AWS. You can also use
  [other types of packaging](https://docs.stacktape.com/configuration/packaging/#packaging-lambda-functions).
- **ConnectTo list** - we are adding dynamo table `mainDynamoDbTable` into `connectTo` list. By doing this, Stacktape
  will automatically setup necessary IAM permissions for the function's role as well as inject relevant environment
  variables into the runtime (such as table name).
- **Events** - Events determine how is function triggered. In this case, we are triggering the function when an event
  (HTTP request) is delivered to the HTTP API gateway:

  - if URL path is `/posts` and HTTP method is `POST`, request is delivered to `savePost` function.
  - if URL path is `/posts` and HTTP method is `GET`, request is delivered to `getPosts` function.

  The event(request) including the request body is passed to the function handler as an argument.

```yml
savePost:
  type: function
  properties:
    packaging:
      type: stacktape-lambda-buildpack
      properties:
        entryfilePath: ./src/lambdas/save-post.ts
    memory: 512
    connectTo:
      - mainDynamoDbTable
    events:
      - type: http-api-gateway
        properties:
          httpApiGatewayName: mainApiGateway
          path: /post
          method: POST

getPosts:
  type: function
  properties:
    packaging:
      type: stacktape-lambda-buildpack
      properties:
        entryfilePath: ./src/lambdas/get-posts.ts
    memory: 512
    connectTo:
      - mainDynamoDbTable
    events:
      - type: http-api-gateway
        properties:
          httpApiGatewayName: mainApiGateway
          path: /posts
          method: GET
```

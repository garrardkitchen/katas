---
title: Introduction
type: docs
---

# List of katas, ideas and suggestions for katas.

{{< columns >}}

## Katas

- [idempotent-consumer](posts/idempotent-consumer) - a consumer that filters out duplicate messages
- [react-function-components](posts/react-function-components) - a mini react app created using function components
- [react-express-socketio](posts/react-express-socketio) - a mini react app created using function components that communicates with nodejs express server using websockets (socker.io)
- [lerna](posts/lerna) - configure a monorepo using lerna
- [typescript-jest](posts/ts-jest) - configure and run a TypeScript and Jest project

<--->

## Ideas

- []() Create a Twilio Serverless solution to send Sms and process response. Create a question that prompts for an answer.  If the answer is correct, send a `congratulatory` response. If incorrect, send a `commiserations` response.  Include secure HTTP endpoint as advanced 

- []() Create a Twilio Serverless solution that calls out to external HTTP API to enrich an inbound channel communication

- []() Create an Azure Functions HTTP Trigger using Serverless Framework (nodejs and .NET Core)

- []() Create an Azure Functions RabbitMQ Exchange deployed to Azure Web App Services Container Trigger using Serverless Framework (node js and .NET Core)

- []() Create a local Kubernetes cluster and deploy a microservice and expose it to be accessed from your local network.

- []() Create a Kubernetes deployment, with front-end, microservice, caching and NoSql engine.

- [net-core-web-app](posts/net-core-web-app) Create a .NET Core C# web application that renders a list of random names [api](http://names.drycodes.com/10?combine=4). Load Names from an API, where the URI for API is set in an appSettings file.  Use the Configuration IOptions pattern and the HttpClientFactory factory class. Create a test using Moq and xUnit, and return Stub from HttpMessageHandler.  Use a different API URI per environment.  

- [net-core-web-app-docker](posts/net-core-web-app-docker) Create a Redis Caching layer for [net-core-web-app](posts/net-core-web-app).NET Core random name web application.  Have a TTL of 10 seconds.  Host in Docker container.  Create an Kubernetes deployment manifest. Refs: [deployment example](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

- []() Create an nodejs app with (1) unit tests using TDD approach with Jest and (2) load test using artillery. Host in Kubernetes via deployment manifest. 2 tiers: Web and Db.

{{< /columns >}}

## Suggestions

- terraform 

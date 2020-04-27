---
title: "Idempotent Consumer"
date: 2020-04-27T15:07:50+01:00
tags: [design patterns, cloud, eda]
---

**Requirements**:

1. Create a consumer that accepts different message reference types that each contains one of these properties:
   - A message that contains an Id
   - A message that contains a TTL
   - A message that contains a before and after _state_

2. The consumer must filter out any duplicate message that contains an Id that has already been processed

3. The consumer must filter out any messages that have expired (TTL)

4. The consumer must filter out messages where the before _state_ does not match the current domain entity state

**Advanced 1**:

5. Create a client that sends messages to the service. The above consumer will be used by the service

6. Fire and forget 10000 messages of each type using Artilery.io
   - Must not receive 400 or 500 status codes

**Advanced 2**:

7. The consumer must be resilient

8. The consumer must be durable

**Tech**:

- .NET Core c# 3.1
- xUnit
- Moq
- Docker (Kubernetes is preferable)
- gRPC for service to service (see 5 above) calls
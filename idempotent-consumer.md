# idempotent consumer

**Requirements**:

1. Create a consumer that accepts  different message reference types that each contain one of these properties :
   - A message that contains an Id
   - A message that contains a TTL
   - A message that contains a before and after state change

2. The consumer must filters out any duplicate message that contain an Id that has alread been processed

3. The consumer must filter out any messages that have expired (TTL)

4. The consumer must filter out messages where the before state does not match the current domain entity state

**Advanced 1**:

5. Create a client that sends messages a service

6. Fire and forget 10000 messages of each type using Artilery.io
   - No 400 or 500 status codes

**Advanced 2**:

7. The consumer must be resilient

8. The consumer must be durable

**Tech**:

- .NET Core c# 3.1
- xUnit
- Moq
- Docker (Kubernetes is desirable)
- gRPC for service to service (see 5 above) calls
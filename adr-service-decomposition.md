# Service decomposition

## Status
accepted

## Context
Given that we have chosen microservices architectural style, one of the things to decide was whether to go with coarse grained services or very fine grained services. This will have impact on aspects like initial cost, latency, need for devops expertise, scalability.  

## decision
- We decided to keep the services slightly coarse grained by combining related functionalities into one deployable unit, given the smaller scale initially.
- The service decomposition is based 
  - on how closely the functionalities are related to each other, depending on the interactions between them. This will help reduce the overall latency.
  - their scalability concerns. The features should have similar scalability concerns
- Moreover the functionalities should be modular enough, like in service based architecture, so that its easy to split them up in future if required.
- Lesser deployable units will reduce initial devops efforts.


## consequences
- We might accidently couple the functionalities in the course of regular development and make it hard for us to decouple them in future. We should try to mitigate this with proper architecture and design review process.
- If the need for splitting the services further arrives sooner, then that will add to the cost a bit. But going by the information we have now, we think that the chances of that happening are pretty low.

Open on [websequencediagrams.com](https://www.websequencediagrams.com/)

```text
title Retiring an Asset (ASE.004)


# ASE.004
participant Publisher
participant Agent
participant Orchestrator
participant Dec VM
participant Ocean DB

Publisher->Agent: Asset Register request

Agent->Agent: Input validation

Agent-->Publisher: HTTP 400 (Invalid user)


Agent->+Orchestrator: Retire Asset

Orchestrator->Dec VM: Retire Asset
Dec VM->Dec VM: Access Control
Dec VM-->Orchestrator: Forbidden
Orchestrator-->Agent: Forbidden
Agent-->Publisher: HTTP 401 (Forbidden)

Dec VM->Orchestrator: ACK
Orchestrator-->Ocean DB: Retire Asset (* optional)
Ocean DB-->Orchestrator: ACK

Orchestrator->-Agent: ACK

Agent->Publisher:  HTTP 202 (Asset)



```
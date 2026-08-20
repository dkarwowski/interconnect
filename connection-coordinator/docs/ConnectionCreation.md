# Connection Creation

## Overview

**Connection** resources are created as part of customer requests. These are
identified by a UUID, used in the activation key that a customer passes from
one provider to another.

In the terminology of this document, the **Passive Provider** is the one who
generates the key and implements the _server_ side of the specification. The
**Active Provider** accepts an activation key from the customer to implement
the _client_ side of the specification.

```mermaid
sequenceDiagram
  actor Customer
  participant A as Active Provider
  participant P as Passive Provider

  Customer->>P: Create resource
  P-->>Customer: base64 Activation Key
  Customer->>A: Create with base64 Key
  A->>P: ConfirmActivationKey
  P-->>A: 200 OK, valid: true
  activate A
  A->>P: CreateConnection
  P-->>A: 200 OK
  A-->>Customer: Creating
  Note over Customer, A: The remaining process is expected to happen asynchronously.
  A->>P: GenerateFeatureGuidance
  P-->>A: 200 OK, ...
  loop For each channel on the parent Interconnect
    Note over A: Reserve Feature params
    A->>P: CreateFeature
    P-->>A: 200 OK
  end

  Note over A, P: Feature finalization + connection verification.
  A-->>Customer: Usable connection
  P-->>Customer: Usable connection

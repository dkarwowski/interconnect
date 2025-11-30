# Security and Operational Excellence Policy

This policy establishes the security and operational excellence requirements for the Cloud Connection Management API specification, which enables multicloud direct connections between cloud service providers. As an openly licensed specification under Apache 2.0, we encourage broad adoption and contribution from the cloud provider community.

To maintain the integrity, security, and reliability of implementations, we have established this policy to define minimum standards that all specification changes must adhere to. This ensures that while the specification remains open and adaptable, critical security and operational capabilities are preserved across all implementations.

The primary goals of this policy are to:
1.	Protect customer data traversing multicloud connections
2.	Ensure consistent security practices across all implementing cloud providers
3.	Maintain operational reliability for mission-critical workloads
4.	Provide clear guidance for contributors proposing specification changes

All proposed changes to the specification must comply with these requirements. The project Maintaining Organizations will evaluate contributions against these standards to preserve the security-first design and operational excellence principles that are foundational to this initiative. Per the Governance Framework, this policy will be reviewed annually to ensure that these tenets are still necessary to achieve the project’s performance and security objectives.

## Core Security Tenets

### Mandatory Encryption
- No changes that make encryption optional or weaken encryption standards will be accepted.
- At least TLS 1.3 must be used for all API communications between providers.
- Connection features that support encryption (like MACsec) must remain mandatory where specified.

###  Authentication and Authorization
- All API endpoints must implement authentication mechanisms that follow encryption and security best practices, such as AWS’ Well-architected recommendations and in particular the Security and Operational Excellence Pillars https://aws.amazon.com/architecture/well-architected/ and Google’s Well-Architected Framework: Security, privacy, and compliance pillar https://docs.cloud.google.com/architecture/framework/security.
- The specification must maintain clear provider identity verification.
- The security sections in API paths must not be emptied or weakened.
- Activation key validation must remain a required step in connection establishment.
- Confused Deputy Resolution is required and any changes suggesting its removal from any API will not be accepted.

### Connection Integrity
- The activation key mechanism must be preserved to ensure proper connection authorization.
- Key material must remain properly secured and obfuscated as specified.
- No changes that bypass activation key validation will be accepted, unless replaced with an objectively stronger mechanism.

### Secure Channel Management
- The MACsec manager provider role must be maintained to ensure proper encryption key management.
- Channel security features must not be removed to simplify implementation.

## Operational Excellence Tenets

### Service Reliability
- Maintenance event notifications must remain part of the specification.
- Connection status monitoring capabilities must be preserved.
- The specification must maintain support for administrative status controls.

### Resource Management
- Bandwidth allocation mechanisms must be preserved.
- No APIs for bandwidth reservations will be accepted.
- Connection resource cleanup requirements (e.g., 7-day deletion policy) must be maintained.
- Adherence to Activation Key lifetimes is required.
- Capacity planning features must not be removed from the specification.

### Fault Isolation
- Channel diversity requirements must be maintained.
- The obfuscated device ID mechanism must be preserved to ensure proper diversity tracking.
- No changes that would compromise redundancy capabilities will be accepted.

## Implementation Requirements

### Specification Compliance
- All implementations must support the full API specification.
- Any additional API features are considered optional, but if implemented, must be implemented in full.
- Implementations must maintain all required fields marked as such in the specification.

### Feature Compatibility
- All implementations must support the defined feature types.
- The L3 base feature configuration must be fully implemented.
- No changes that would break interoperability between providers will be accepted.

### Protocol Standards
- BGP session security features must be preserved.
- MTU and VLAN configuration capabilities must be maintained.
- IP subnet management features must be fully implemented.

## Change Management Policy

### Security Impact Assessment
- All proposed changes must include a security impact assessment.
- Changes that reduce security capabilities will be rejected.
- Security considerations must take precedence over implementation simplicity.

### Backward Compatibility
- Changes must maintain backward compatibility where possible.
- Breaking changes must provide clear migration paths.
- Version management must follow semantic versioning principles.

### Documentation Requirements
- All changes must include appropriate documentation updates.
- Security implications must be clearly documented.
- Implementation guidance must be provided for security-critical features.


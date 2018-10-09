# IAM overview

EnOS applies the identity and access management (IAM) scheme to support multi-tenancy, where each tenant in EnOS is managed as an organizational unit.  Data that belongs to different organizations are securely segregated and can only be accessed by users that are registered to the organization.

The built-in IAM schemes of EnOS provide capabilities of identity management, authentication, authorization.

## Identity management

With IAM, a hierarchy structure is introduced to represent the relationship that exists within an organization. Each tenant is identified as an organizational unit (OU).

EnOS offer the following types of identities:
- *User accounts* are usually created for EnOS Portal users and operations staff.
- *Service accounts* (a.k.a. App tokens) are assigned to applications, to access EnOS service APIs.
- *Device identities* are assigned to all devices and edges that connect to EnOS Cloud.

All identities are created under OUs. Each OU has a unique owner and optionally administrators. IAM also provides capability of integrating with external user registries that supports LDAP, such as Windows Directory Service.

## Authentication

IAM provides different authentication methods for different account types.

- User account is required to access to EnOS Portal with valid credential (user identifier and password). Strong password with required complexity enforced by security policy managed by OU administrators. Multi-factor authentication is available as a configurable security option.

- Service accounts use access keys (i.e. digital signatures) to perform authentication with EnOS.

- Devices and edges use X.509 certifications to establish the secure data communication tunnels with EnOS Cloud. Devices with TPM chips will be authenticated with its encrypted certifications stored in the hardware.

## Authorization

EnOS adopts Role-Based-Access-Control (RBAC) that is a policy neutral access control mechanism defined around roles and privileges. Access control rule is defined as a 3-tuples in the form of role-permission-resource. The resource includes the following:

- Applications: applications that a role has access to
- User Interface: menu items or buttons that a role can see
- API: APIs that a role can invoke
- Data: data that a role can read or write
- Reports: reports that a role can read
- Events: events from an application that a role can view or handle

IAM allows OU administrator to define access control rules to grant privileges/ permissions of resources to other accounts through the IAM graphic user interface or through the APIs.

Accounts with proper privileges granted may access the corresponding resources via EnOS service APIs or Portal. Access control validation is performed by IAM service for each access attempt.

# Security overview

Solid security practices and principles are core to the design of EnOS to ensure that the confidentiality, integrity, and availability of your systems and data is maintained at all times.

## Authentication
Access to the EnOS service APIs and portal require authentication. EnOS provides integration with GovTech’s user registries that supports LDAP, such as Windows Directory Server.
EnOS uses several types of credentials for authentication. These include (1) passwords, (2) cryptographic keys, (3) digital signatures, and (4) certificates. EnOS also provides option of requiring (5) multi-factor authentication for EnOS Portal login.

### Passwords
Passwords are required for accessing to EnOS Portal. Password complexity policy will be applied to force users to create strong passwords that cannot be easily guessed.

### Multi-factor Authentication (MFA)
MFA is an additional layer of security for accessing EnOS Portal. When this optional feature is enabled, user will be prompted to provide a 6-digit single-use code in addition to user name and password credentials before access is granted. User gets this single-use code via SMS or email.

### Access Key
EnOS requires that all API requests be signed – that is, they must include a digital signature that EnOS Cloud can use to verify the identity of the requestor. Application developers calculate the digital signature using a cryptographic hash function. The input to the hash function in this case includes the text of request and the secret access key.
Not only does the signing process help protect message integrity by preventing tampering with the request while it is in transit, it also helps protect against potential replay attacks. A request must reach the EnOS services within 15 minutes of the time stamp in the request. Otherwise, the request will be denied.
 
### Key Pairs
The virtual machine instances are created with a public/private key pair rather than a password for signing in via Secure Shell (SSH). The public key is embedded in the virtual machine instance, and users use the private key to sign in securely without a password.

### X.509 Certificates
X.509 certificates are used to sign SOAP-based requests. X.509 certificates contain a public key and additional metadata (like an expiration date that EnOS verifies when applications upload the certificate) and is associated with a private key.
When an application creates a request, it creates a digital signature with the private key and then include that signature in the request, along with the certificate.

EnOS verifies the sender by decrypting the signature with the public key that is in the certificate. EnOS also verifies that the certificate the application sent matches the certificate that are uploaded.

## Certificate Authority
EnOS has built-in industry-standard Certificate Authority service for certificate management purpose. It provides a series of fundamental CA service APIs, including CA setup, certificate issue, certificate renew, certificate revoke and certificate status query.
Certificates for different purposes may be requested and issued from EnOS CA service. Corresponding operation may be completed through API invokes in seconds. Both CRL distribution and OSCP stapling with high availability is supported.

## Role-based Access Control
EnOS adopts Role-Based-Access-Control (RBAC) that is a policy neutral access control mechanism defined around roles and privileges. Access control rule is defined as a 3-tuples in the form of role-permission-resource.
Within an organization, roles are created for various job functions. The permissions to perform certain operations are assigned to specific roles.
Members or staff (or other system users) are assigned roles, and through those role assignments acquire the computer permissions to perform certain computer-system functions.
Since users are not assigned permissions directly, but only acquire them through their role (or roles), management of individual user rights becomes a matter of simply assigning appropriate roles to the user's account; this simplifies common operations, such as adding a user, or changing a user's department.

## Network Protection
For greater communication security when accessing EnOS Portal, devices and end users must use HTTPS for data transmissions. HTTPS uses the SSL/TLS protocol, which uses public-key cryptography to prevent eavesdropping, tampering, and forgery. Public trusted CA issued web server certificates should be deployed to enable this feature.

All EnOS services provide API endpoints that allow devices and end users to establish secured communication sessions. For RESTful APIs, HTTPS is used. For SSL/TLS protected data channel between devices and EnOS cloud cluster, X.509 certification based bidirectional authentication is adopted, all data is encrypted during transfer.

## Data Encryption
EnOS adopts a very strict way for protecting data at rest. Sensitive data is encrypted before putting into files or databases. Data is encrypted with a key generated by the platform or with a key customers supply.

Decryption happens automatically when data is retrieved through the platform API. Therefore, no intruders or platform operators will have access to the data even when they have access to the underlying file system or database systems.

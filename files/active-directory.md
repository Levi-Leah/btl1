# Active directory

## Features

- **Authentication**
  - **Purpose**: Provides a secure way for employees to log into the network using provisioned user accounts.
  - **Features**:
    - Account locking to prevent unauthorized access.
    - Automatic locking after a set number of unsuccessful login attempts.

---

- **Authorization**
  - **Purpose**: Controls access to resources based on user account permissions and group memberships.
  - **Features**:
    - Determines what resources a user can access.
    - Specifies actions users are allowed to perform.

---

- **Centralized Management**
  - **Purpose**: Enables efficient management of resources across the domain.
  - **Features**:
    - Centralized control of user accounts, computers, printers, and security policies.

---

- **Group Policy**
  - **Purpose**: Allows administrators to define and manage settings for users and computers across the network.
  - **Features**:
    - Enforce security settings.
    - Manage software installation.
    - Configure desktop settings across the network.

---

## Objects and Organizational Units

- In Active Directory (AD), an object is a digital representation of a resource within the network, such as users, computers, groups, printers, or shared folders.

![](images/Screenshot%20from%202024-12-16%2015-31-52.png)

---

### Key Features of Active Directory Objects

- **Attributes**:
  - Each object has attributes that describe its properties.
  - Attributes may include job role, manager details, group memberships, or security settings.

- **Globally Unique Identifier (GUID)**:
  - Every object is assigned a GUID that remains constant, even if the object is renamed or moved within AD.

- **Distinguished Name (DN)**:
  - Reflects the object's location in the AD hierarchy.
  - The DN changes if the object is relocated.

- **Object Classes**:
  - Objects belong to specific classes, defining the attributes they can have.
  - Example classes:
    - `User` for user accounts.
    - `Computer` for domain-joined computers.

---

### Types of Objects in Active Directory

- **User Objects**
  - Represent individual users.
  - Store:
    - Usernames.
    - Passwords.
    - Personal details.
    - Group memberships.
  - Security Identifier (SID):
    - Unique to each user account.
    - Remains the same if the user is renamed.
    - Changes if the account is deleted and recreated.

- **Computer Objects**
  - Represent computers within the domain.
  - Manage:
    - Policies.
    - Permissions.
    - Security settings.
  - SID:
    - Unique for each computer within the domain.
    - Remains constant even if the computer is renamed.

- **Group Objects**
  - Represent collections of users or computers.
  - Simplify management by assigning permissions to a group rather than individual users.
  - Types:
    - **Security Groups**: Assign permissions and rights to resources.
    - **Distribution Groups**: Used for email distribution lists (no security permissions).

- **Organizational Units (OUs)**
  - Containers used to organize objects within a domain.
  - Can hold:
    - User accounts.
    - Groups.
    - Computers.
    - Other OUs.
  - Enable:
    - Delegated administration.
    - Application of Group Policies.
  - **Example**: A Finance OU could include user accounts and computers for the Finance team.

- **Printer Objects**
  - Represent network printers.
  - Store printer configurations and permissions.

- **Shared Folder Objects**
  - Represent shared resources, such as file shares.
  - Manage access and permissions for shared folders.

---

- **Security Identifiers (SIDs)**
  - **Purpose**: Uniquely identify objects within the domain for security purposes.
  - **Structure**:
    - **Domain SID**: Common across all objects in the domain.
    - **Relative Identifier (RID)**: Unique portion distinguishing each object.

  - **Example**:
    - Domain SID:   `S-1-5-21-123456789-987654321-123456789`.
    - User SID:     `S-1-5-21-123456789-987654321-123456789-1000`.
    - Computer SID: `S-1-5-21-123456789-987654321-123456789-1001`.

Each object has the same Domain SID but a unique RID, ensuring distinct identifiers.

---

## Searching AD Objects

During investigations, you may need to gather detailed information about Active Directory (AD) objects, particularly user accounts. This could involve tasks such as:

- Checking if accounts are disabled.
- Reviewing password settings.
- Retrieving descriptive information.
- Identifying group memberships.

There are two primary methods for querying AD objects:

- PowerShell
- Lightweight Directory Access Protocol (LDAP)

---

### Using PowerShell

- **Basic Search Command**
  - **Command**: `Get-ADUser -Identity "NameHere" -Properties *`
  - **Explanation**:
    - Retrieves all properties of a specified AD user.
    - The `*` wildcard fetches all available properties (often an overwhelming amount of data).

- **Key Properties**
  - Some commonly useful properties include:
    - `LastLogonTimestamp`: Indicates when the account was last logged into.
    - `LockedOut`: Specifies if the account is currently locked.
    - `MemberOf`: Lists the groups the user belongs to.
    - `Modified`/`modifyTimeStamp`: Shows when the account was last modified.
    - `PasswordExpired`/`PasswordLastSet`: Shows when the password was last set or modified.

- **Filtering Properties**
  - To reduce clutter, you can specify only the properties of interest:
    - **Command**:  `Get-ADUser -Identity "NameHere" -Properties LastLogonDate,LockedOut,Modified,PasswordExpired,PasswordLastSet`
    - **Explanation**: Retrieves the specified properties instead of all properties, making the results more manageable.

---

### Using LDAP

- **LDAP (Lightweight Directory Access Protocol)**
  - A protocol for accessing and managing directory services over a network. It is commonly used by users and applications to interact with AD.

- **GUI Tools for LDAP**
  - Many software tools provide graphical interfaces to simplify interaction with LDAP. One example is the **Softerra LDAP Browser**, which is free to use.

---

## Domain Controllers

A **Domain Controller (DC)** is a server that hosts the Active Directory Domain Services (AD DS) role. It plays a critical role in managing the domain, ensuring authentication, access control, and directory services across the network.

---

### Key Functions of a Domain Controller

- **Authentication**:
  - Validates user credentials during logon requests.
  - Compares the username and password against stored credentials in Active Directory.

- **Authorization**:
  - Determines what resources a user can access after authentication.
  - Enforces security policies based on permissions and group memberships.

- **Access to the Active Directory Database**:
  - Stores information about all objects in the domain, such as users, computers, and groups.
  - Provides access to this directory for users and applications, either locally or remotely via protocols like LDAP.

- **Group Policy Enforcement**:
  - Applies policies across the domain, including:
    - Security settings.
    - Software installations.
    - User and computer configurations.

- **Replication Across DCs**:
  - In multi-DC environments, changes made on one DC (e.g., creating or modifying a user account) are replicated to other DCs.
  - Ensures consistency and redundancy within the domain.

---

### Types of Domain Controllers

- **Primary Domain Controller (PDC)**
  - **Role**:
    - Acts as the main DC for managing critical operations, such as password changes.
    - In modern Windows environments, the **PDC Emulator** role is used for backward compatibility with older Windows systems.
  - **Key Feature**: Ensures central coordination for certain domain operations.

- **Backup Domain Controller (BDC)**
  - **Role**:
    - Used in older Windows NT environments to provide redundancy.
    - Holds read-only copies of the user accounts database.
  - **Modern Alternative**: Multi-master replication in newer environments allows all DCs to read and write data, making traditional BDCs obsolete.

- **Read-Only Domain Controller (RODC)**
  - **Role**:
    - Holds a read-only copy of the Active Directory database.
    - Useful for branch offices or locations with limited physical security.
  - **Limitations**:
    - Can authenticate users but cannot make changes to the directory.
    - Enhances security in environments where full DC access might pose risks.

---

## AD Structure Examples

### Single Domain Example


![](images/Screenshot%20from%202024-12-16%2016-02-51.png)

In a **single domain** setup, all resources and objects are contained within a single domain. For example:

**Domain**: `securityblue.team`  
**Components**:

- **Domain Controller Server**: `SBTDC01` the manages the domain.
- **Organizational Units (OUs)**:
  - **HR OU**: Contains user accounts for HR employees.
  - **Finance OU**: Contains user accounts for Finance employees.
  - **Corporate OU**: Contains all employee computers.

This structure is simple and suitable for smaller organizations with centralized management needs.

---

### Multi-Domain Example (Tree/Forest)

![](images/Screenshot%20from%202024-12-16%2016-00-45.png)

In a **multi-domain** structure, subdomains are created under a root domain to organize resources and departments. For example:

**Root Domain**: `NotARealCompany`  
**Subdomains**:
- `finance.NotARealCompany`: Contains OUs for Finance resources.
- `engineering.NotARealCompany`: Contains OUs for Engineering resources.

**Key Notes**:

- Each domain can have its own organizational units.
- Even with a single tree of domains, the structure is referred to as an **Active Directory Forest**.

---

### Multi-Root Domain Example (Forest)

![](images/Screenshot%20from%202024-12-16%2016-05-05.png)

A **multi-root domain forest** occurs when multiple root domains are combined. This setup is common during mergers and acquisitions. For example:

**Scenario**:

- `NotARealCompany` acquires `FakeCompany`.  
- Each company retains its own domain but integrates into a shared forest.

**Benefits of an AD Forest**:

- Domains operate independently.
- Shared configuration across domains.
- Security and trust relationships can be established, allowing:
  - Users from `FakeCompany` to access resources on `NotARealCompany` servers.
  - Centralized management while maintaining domain autonomy.

**Example Structure**:

- Root Domains:  
  - `NotARealCompany`
  - `FakeCompany`
- Subdomains:  
  - `finance.NotARealCompany`
  - `engineering.NotARealCompany`

This structure allows large organizations to maintain scalability and flexibility across different domains while enabling secure collaboration.

---

## Security Groups

**Security Groups (SGs)** in Active Directory (AD) are used to group users or other AD objects (e.g., computers) and assign permissions collectively. Unlike Organizational Units (OUs), which are used for administrative organization and Group Policy application, Security Groups focus on **access control**.

---

### Key Features of Security Groups

- **Purpose**:
  - Simplifies permission management by assigning access rights to groups rather than individual users.
  - Supports the principle of least privilege by ensuring that users only have access to resources necessary for their roles.

- **Differences from OUs**:
  - **Security Groups**: Used for access control.
  - **Organizational Units**: Used for logical organization and administrative purposes.

---

### Naming Structure for Security Groups

While AD does not enforce a specific naming structure, organizations typically use in-house naming conventions for clarity. A consistent structure helps identify the purpose of a security group at a glance.

**Example Naming Convention**:

| Element       | Example               | Description                                                     |
|---------------|-----------------------|-----------------------------------------------------------------|
| **Prefix**    | `SG-`                | Identifies the object as a security group.                     |
| **Department**| `HR`, `IT`, `Marketing` | The department associated with the group.                      |
| **Permission**| `ReadOnly`, `Write`, `FullAccess` | Indicates the permission level assigned to the group.           |
| **Location**  | `London`, `NewYork`  | (Optional) Specifies the geographic location of the group.     |

**Examples**:

- `SG-IT-FullAccess-London`
- `SG-Marketing-ReadOnly-Singapore`
- `SG-Security-FullAccess-Global`

---

## Group Policy

- Group Policy allows administrators to define and enforce rules, settings, and security configurations for users and computers in a network. It automates policy management, ensuring consistent configurations and security across hundreds or thousands of devices.
- Group Policy settings can be stored either locally on a computer or in Active Directory.
- When used with AD, these settings are grouped into a Group Policy Object (GPO).
- **Group Policy Object (GPO)**: GPO is a collection of rules that define security settings, permissions, and configurations applied to users and computers in the network.

---

### Types of GPOs

| **Type**          | **Description**                                                                                     | **Example**                                                                                   |
|--------------------|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| **Local GPOs**     | Apply to a single computer only, regardless of its network or domain membership.                    | Setting a local password policy on a standalone PC.                                           |
| **Non-Local GPOs** | Stored in Active Directory, apply to multiple users and computers in a domain environment.          | Disabling USB ports for all employees in the "Workstations" group.                            |
| **Starter GPOs**   | Templates with pre-configured settings to help admins create new GPOs faster.                       | Using a starter GPO for remote workers with pre-configured security settings.                 |

---

### GPO Processing Order

The order in which Group Policies are applied determines the final configuration for a user or computer. The **LSDOU hierarchy** (Local, Site, Domain, Organizational Unit) applies:

1. **Local Policies**: Applied first, configured on individual computers.
2. **Site-Level Policies**: Applied next if configured.
3. **Domain-Level Policies**: Applied across the domain.
4. **Organizational Unit (OU) Policies**: Applied in order from the highest-level OU to the most specific nested OU.

#### Conflict Resolution

- **Last Applied Wins**: If two policies conflict, the one applied last (closest to the object) takes effect.
- **Enforced GPOs**: Overrule all other policies, regardless of the hierarchy.  
  - Example: If a domain-level GPO allows USB access but an OU-level GPO blocks it, the OU-level policy will take effect unless the domain-level policy is **enforced**.

---

## Authentication and Security

Active Directory (AD) authentication mechanisms are essential for securing access to network resources. These mechanisms ensure users are verified before accessing services like file servers, email, or intranet systems. AD employs various authentication methods, including **Kerberos**, **NTLM**, and **LDAP**, which are supported by best practices to maintain a secure environment.

---

### AD Authentication Mechanisms

#### Kerberos Authentication

![](images/Screenshot%20from%202024-12-16%2021-19-33.png)

Kerberos is a secure, ticket-based authentication system that allows users to access multiple services after logging in once.

**How Kerberos Works**:

1. **Login Request**: A user logs in, and their computer sends a request to the Key Distribution Center (KDC)’s Authentication Server (AS) for a Ticket Granting Ticket (TGT).
2. **TGT Issuance**: If credentials are correct, the AS sends back an encrypted TGT.
3. **Service Request**: When accessing a resource (e.g., email), the TGT is used to request a service ticket from the Ticket Granting Server (TGS).
4. **Service Ticket Issuance**: The TGS issues a service ticket specific to the requested resource.
5. **Resource Access**: The service ticket is presented to the application server, which validates it and grants access.

---

#### NTLM (NT LAN Manager)

![](images/Screenshot%20from%202024-12-16%2021-25-03.png)

NTLM is an older Windows authentication protocol using a challenge-response mechanism to verify user identity without sending passwords over the network.

**How NTLM Works**:
1. A user attempts to access a resource, and the server sends a challenge (random number).
2. The user's computer encrypts the challenge using a hashed version of their password and sends the response to the server.
3. The server verifies the response. If correct, access is granted.

**Drawbacks**:

- Less secure than Kerberos due to vulnerabilities in older implementations.

---

#### 3. LDAP (Lightweight Directory Access Protocol)

![](images/Screenshot%20from%202024-12-16%2021-27-03.png)

LDAP is used to authenticate users and control access by communicating with a centralized directory service like AD.

**How LDAP Works**:

1. A user submits their credentials (username and password) via a **bind request** to the LDAP server.
2. The LDAP server validates the credentials and responds with a **bind result** indicating success or failure.
3. If successful, the user can request access to resources. The LDAP server grants or denies access based on permissions.

**Advantages**:

- Centralizes authentication for consistent access control.

---

### Best Practices for AD Security

- **Regular Auditing and Monitoring**
  - **Purpose**: Detect unauthorized access, modifications, or suspicious behavior.
  - **Implementation**:
    - Monitor Windows Event logs for authentication failures or unusual activity.
    - Set up alerts for changes to sensitive AD objects.

- **Least Privilege Principle**
  - **Definition**: Provide users with the minimum access necessary to perform their roles.
  - **Benefits**:
    - Limits potential damage from compromised accounts.
    - Reduces the attack surface.

- **Segregation of Duties**
  - **Definition**: Divide responsibilities to prevent a single person from having complete control over critical processes.
  - **Example**:
    - One person creates user accounts.
    - Another approves changes to security settings.
  - **Purpose**: Minimizes the risk of insider threats and misuse of privileges.

---

- **Patch Management**
  - **Definition**: Regularly update AD servers and related software to address vulnerabilities.
  - **Key Points**:
    - Apply patches promptly after release by software vendors.
    - Prioritize updates for critical systems and known vulnerabilities.
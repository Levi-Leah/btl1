# Management principles

## Risk

- **Definition**: The possibility of a negative impact on any aspect of an organization, such as business, financial, or security.
- **Key Components**:
  - **Vulnerability**: A weakness that can be exploited by a threat. Vulnerabilities can be managed whereas a threat cannot.
  - **Threat**: A potential danger or adversary. Threats cannot be managed directly but can be mitigated through controls.
- **Risk Management**: The process of applying controls to reduce risk to an acceptable level.
- **Likelihood of Exploitation**: Determined by the presence of a threat, the existence of vulnerabilities, and the effectiveness of controls in place.

---

### Risk Assessments

- **Purpose**:
  - Identify and evaluate risks, including their likelihood and potential consequences.
  - Inform decision-making and compliance with laws or regulations.

---

### Conducting a Risk Assessment

- **Identify Potential Hazards**: Recognize what could cause harm.
- **Identify Who Might Be Harmed**: Determine who or what could be affected.

**Evaluate Risk**: Assess severity and likelihood; establish suitable precautions.
**Implement Controls**: Apply measures to mitigate risks and document findings.
**Review and Reassess**: Periodically update the assessment to reflect changes in circumstances or threats. Risk assessments should be dynamic and evolve with changing environments, particularly in fast-paced fields like cybersecurity.

---

### Managing Risk

Organizations manage risk based on their **risk appetite** and objectives. There are four primary strategies:

- **Risk Mitigation**:
  - Apply technical controls (e.g., patches, firewalls) and administrative controls (e.g., policies, procedures).
- **Risk Transfer**:
  - Shift the potential cost of loss to another party (e.g., through insurance).
- **Risk Acceptance**:
  - Proceed with an activity despite possible harm.
  - Common for unavoidable or low-priority risks.
- **Risk Avoidance**:
  - Prevent an incident entirely by eliminating hazards.
  - The most effective strategy, though not always feasible.

---


## Policies and Procedures

### Policies

- **Definition**: A policy is a high-level plan of intent or course of action within a specific domain, guiding actions and responsibilities.
- **Purpose**:
  - Outlines rules and principles.
  - Defines roles, responsibilities, and accountability.
  - Provides clear guidance for actions and expected behavior.
- **Hierarchy**:
  - Policies are at the highest level, followed by procedures, standards, and guidelines.
- **Importance in Organizations**:
  - Employees must read and adhere to organizational policies, such as acceptable use policies (AUPs).
  - Policies often interlink and may include sub-policies, requiring employees to be familiar with those relevant to their roles while knowing where to find others.

---

### Common Policy Examples

- **Acceptable Use Policy (AUP)**:
  - Stipulates what users can and cannot do on corporate, university, or ISP networks.
  - Governs behavior (e.g., no social media or adult content) and outlines consequences for violations (e.g., loss of privileges).

- **Service Level Agreement (SLA)**:
  - Defines the commitments between a service provider and a customer.
  - Includes:
    - Services provided.
    - Performance levels.
    - Response times for issues.
    - Consequences for failing to meet service levels.

- **Bring Your Own Device (BYOD)**:
  - Outlines rules for using personal devices (e.g., laptops, phones) on corporate networks.

- **Memorandum of Understanding (MOU)**:
  - A formal agreement between two or more parties that is **not legally binding**.
  - Typically precedes a binding contract.

---

### Standard Operating Procedures (SOPs)

- **Definition**: A step-by-step set of instructions for routine tasks, designed to ensure:
  - Effectiveness.
  - Efficiency.
  - Compliance with regulations.
  - Reduces errors, miscommunication, and non-compliance.
  - Creates uniformity within an organization by standardizing tasks.
  - Periodically reviewed and updated.
  - Tested before implementation.
  - Easily accessible to all team members.
  - Local or branch-specific variations may exist to comply with regional laws or conditions.

---

## Compliance and Frameworks

Organizations must follow security frameworks to meet minimum security standards and comply with industry-specific legislation and regulations.

- **Definition**: Adherence to rules and requirements specified by a framework or regulation.
- **Purpose**
  - Ensures organizations meet legal and regulatory standards while maintaining a high level of security.
  - **Builds Trust**: Customers and partners value organizations that follow recognized frameworks.
  - **Legal Requirement**: Non-compliance can result in significant legal and regulatory fines.
  - **Improves Security**: Reduces risk by ensuring organizations are better prepared to handle security incidents.

### Key Compliance Frameworks

#### General Data Protection Regulation (GDPR)

- **Scope**: Governs data protection and privacy in the EU and EEA, and the transfer of data outside these regions.
- **Key Requirements**:
  - Controllers/processors must implement technical and organizational measures to protect data.
  - No personal data may be processed unless this processing is done under one of six lawful bases specified by the regulation (consent, contract, public task, vital interest, legitimate interest, or legal requirement). When the processing is based on consent the data subject has the right to revoke it at any time.
  - Data controllers must clearly disclose any data collection, declare the lawful basis and purpose for data processing, and state how long data is being retained and if it is being shared with any third parties or outside of the EEA.
  - Data subjects have the right to request a portable copy of the data collected by a controller in a common format, and the right to have their data erased under certain circumstances
  - Businesses must report data breaches to national supervisory authorities within 72 hours if they have an adverse effect on user privacy.
  - Violators of the GDPR may be fined up to €20 million or up to 4% of the annual worldwide turnover of the preceding financial year in case of an enterprise, whichever is greater.
  - Principles include:
    - Pseudonymization or anonymization.
    - Privacy by default (e.g., highest-possible privacy settings).

---

#### ISO 27001

- **Scope**: Global information security standard, part of the ISO/IEC 27000 family.
- **Key Requirements**:
  - Specifies a management system to bring information security under control.
  - Certification available upon successful audit by an accredited body.

---

#### Payment Card Industry Data Security Standard (PCI DSS)

- **Scope**: Applies to organizations handling branded credit cards from major card schemes.
- **Purpose**: Reduces credit card fraud by securing cardholder data.
- **Validation**: Validation of compliance is performed annually or quarterly.
- **Validation Methods**:
  - **Self-Assessment Questionnaire (SAQ)**: For smaller transaction volumes.
  - **External Qualified Security Assessor (QSA)**: For moderate transaction volumes.
  - **Internal Security Assessor (ISA)**: For large transaction volumes; includes issuing a Report on Compliance.

---

#### Health Insurance Portability and Accountability Act (HIPAA)

- **Scope**: Protects Electronic Protected Health Information (ePHI) in the U.S. The primary goal of HIPAA is to protect ePHI which includes, name, dates such as birth, admission, discharge, death, telephone number, SSN, photographs, address, etc.
- **Covered Entities**: Includes healthcare providers, suppliers, and outsourced IT providers handling ePHI.
- **Key Requirements**:
  - **Technical Controls**:
    - Encryption, authentication, password complexity, access auditing, and segmentation.
  - **Procedural Controls**:
    - Password policies, incident response plans, contingency plans, and audit procedures.
  - Risk analysis to evaluate risks to the confidentiality, integrity, and availability of ePHI.

---

## Change and Patch Management

### Change Management

- **Definition**: The process of ensuring organizational changes are:
  - Planned.
  - Supported.
  - Well-documented.
  - Audit-able.
- **Purpose**:
  - Identifies accountability if changes lead to security risks or incidents.
  - Ensures transparency in system updates and security modifications.
- **Key Benefits**:
  - Provides a clear record of changes and the individuals involved.
  - Simplifies troubleshooting and accountability during incidents.

---

### Patch Management

- **Definition**: The process of deploying patches and security fixes to IT assets, such as operating systems, software, and applications.
- **Purpose**:
  - Remediates vulnerabilities in older versions of software.
  - Reduces the risk of exploitation.
  - Ensures compliance with frameworks like **Security Essentials+** (e.g., remediating critical vulnerabilities within 14 days).

---

### Patch Deployment Methods

#### **Windows Server Update Services (WSUS)**

- **Purpose**: Deploys Microsoft updates across a network.
- **How It Works**:
  - A designated "upstream server" connects to Microsoft Update to download patches.
  - The upstream server deploys updates to endpoints and servers, even without direct internet access.

#### **Microsoft System Center Configuration Manager (SCCM)**

- **Purpose**: A paid solution that assists with:
  - Asset inventory.
  - Software installation.
  - Patch deployment.
- **Features**:
  - Uses WSUS for update checks and installation.
  - Provides advanced control over patching schedules and methods.
  - Primarily designed for Windows systems, with limited support for macOS, Linux, and 3rd-party applications.

#### **Commercial Patch Management Solutions**

- **Example**: **ManageEngine Patch Manager Plus**
- **Capabilities**:
  - Deploy patches to Windows, macOS, and Linux systems.
  - Update operating systems, Microsoft Office, and 3rd-party applications (e.g., Adobe, browsers, utilities).
  - Scan endpoints for missing patches and report compliance.
  - Manage patch testing phases to reduce risk for IT teams.

#### **Retroactive Patch Releases**

- Vendors occasionally release patches for unsupported operating systems during critical vulnerabilities.
  - Microsoft released a patch for **Windows XP** in 2019 to mitigate **BlueKeep (CVE-2019-0708)**, despite XP’s end-of-support in 2014.
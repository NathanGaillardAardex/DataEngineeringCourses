# Administer a Microsoft Fabric environment
## Microsoft Fabric Administrator Role Overview

### Understanding the Fabric Administrator Role
- The **Fabric Admin role** (formerly Power BI Admin) is responsible for **managing security, access control, governance, configuration, monitoring, and optimization**.
- **Admins use multiple tools**: Fabric Admin Portal, Microsoft 365 Admin Center, Microsoft Entra ID, PowerShell cmdlets, REST APIs, and monitoring workspaces.

### Key Administrative Tasks

#### 1. **Security and Access Control**
- **Role-Based Access Control (RBAC)**:
  - Define **who can view, edit, and manage** content.
  - Use **Microsoft Entra ID** for user authentication and access control.
  - Set up **data gateways** to securely connect on-premises data to Fabric.

#### 2. **Data Governance**
- Secure **inbound and outbound connectivity** within the tenant.
- Apply **data governance policies** to ensure compliance.
- Monitor **usage and performance metrics** to maintain **data integrity and security**.

#### 3. **Customization and Configuration**
- Configure **private links, tenant security policies, and data classifications**.
- Customize **the look and feel of dashboards and reports**.
- Enable or disable **Fabric for the tenant** via the **Fabric on/off switch**.

#### 4. **Monitoring and Optimization**
- **Monitor Fabric usage and performance** to optimize query execution and system load.
- Configure **alerts and logging** for real-time issue detection.
- Manage **capacity scaling and performance tuning**.

### Key Administrative Tools

#### 1. **Fabric Admin Portal**
- **Central hub for managing Fabric settings**.
- Allows **tenant-wide configuration** and **role assignment**.
- **Key setting: Fabric On/Off Switch** to enable Fabric for Power BI tenants.

#### 2. **PowerShell Cmdlets**
- Automate **group management, data source configuration, and usage monitoring**.
- Example:
  ```powershell
  Get-PowerBIWorkspace -Scope Organization
  ```
- Supports **batch operations and scripting** for repetitive tasks.

#### 3. **Admin APIs and SDKs**
- Use **REST APIs** for automating admin tasks such as **group management, data access, and performance tracking**.
- Example API call to list workspaces:
  ```http
  GET https://api.powerbi.com/v1.0/myorg/groups
  ```
- Supports **OAuth 2.0 authentication** for secure API access.

#### 4. **Admin Monitoring Workspace**
- Provides **feature usage and adoption reports**.
- Helps **identify performance bottlenecks and track resource consumption**.
- Enables **sharing insights with other users in the organization**.

### Summary of Fabric Admin Responsibilities
1. **Security & Access Control** – Manage RBAC, Entra ID, and data gateways.
2. **Data Governance** – Apply security policies and monitor compliance.
3. **Customization & Configuration** – Adjust Fabric settings for organizational needs.
4. **Monitoring & Optimization** – Track performance and optimize resource usage.
5. **Automation & Integration** – Use PowerShell, REST APIs, and SDKs for efficiency.

### Key Takeaways
- **Fabric admins ensure secure, efficient, and optimized use of Microsoft Fabric**.
- **A combination of manual controls and automation tools** helps streamline administration.
- **Monitoring and governance tools** allow proactive issue resolution and compliance enforcement.

## Manage Security in Microsoft Fabric

### Overview
- Security in Microsoft Fabric follows **Power BI security principles**, managing **users, groups, sharing, and content distribution**.
- **Admins ensure compliance, limit access to sensitive data, and optimize license allocation**.

### 1. **Managing Users and Licenses**
- **User licenses** define **access levels and functionality** within Fabric.
- Admins **assign, manage, and revoke** licenses to **control costs and compliance**.
- **License Management is handled via the Microsoft 365 Admin Center**.
- **Types of licenses impact user access**:
  - **Consumer licenses** control visibility of reports and dashboards.
  - **Workspace licenses** define the **capabilities available in a given workspace**.
- **Efficient license management** prevents **unnecessary costs and ensures proper resource utilization**.

### 2. **Managing Content, Sharing, and Distribution**
- **Admins control how users interact with Fabric** (sharing, collaboration, distribution).
- **Best practices for secure sharing**:
  - **Use workspace apps** for report access instead of direct workspace permissions.
  - **Grant least privilege** – provide only necessary access.
  - **Use workspace roles** to define clear collaboration boundaries.
- **Content sharing can be managed internally and externally**, aligning with **corporate security policies**.

### 3. **Enforcing Security and Compliance**
- **Restrict external sharing** if required by company policy.
- **Ensure governance over workspace access** to protect sensitive data.
- **Monitor license allocation and user activity** to prevent security risks.

### Key Takeaways
- **Admins manage user access through Microsoft 365 and enforce sharing policies**.
- **Proper license management ensures cost control and compliance**.
- **Fabric security should follow best practices: least privilege access and secure content distribution**.

## Govern Data in Microsoft Fabric

### Overview
- **Microsoft Fabric includes built-in governance features** to manage data reliability, security, and lineage.
- **Governance tools include**:
  - **Endorsement** (Promoted/Certified content).
  - **Scanner API** for **sensitive data detection**.
  - **Data lineage tracking** for **impact analysis**.

### 1. **Endorse Fabric Content**
- **Endorsement builds trust** in data assets by **marking them as reliable and reviewed**.
- **Types of endorsements**:
  - **Promoted Content** – Marked by a **Promoted badge**, available for workspace members with **Contributor/Admin roles**.
  - **Certified Content** – Requires **formal review** and is marked by a **Certified badge**.
- **Fabric Admins can certify content across the organization**, ensuring **trusted data usage**.

### 2. **Scan for Sensitive Data**
- **Metadata scanning** enables **cataloging and governance** of Fabric items.
- **Scanner API (Admin REST APIs) scans**:
  - **Data warehouses**
  - **Pipelines**
  - **Datasets**
  - **Reports and dashboards**
- **Detects structured & unstructured sensitive data**.
- **Admins must enable metadata scanning** before it can be used.

### 3. **Track Data Lineage**
- **Data lineage tracks the flow of data** across Fabric (Impact Analysis).
- **Lineage View in Workspaces** provides visibility into:
  - **Data origins**
  - **Transformation processes**
  - **Data dependencies**
- **Integrates with Microsoft Purview** for **enterprise-wide data governance**.

### Key Takeaways
- **Endorsement (Promoted/Certified badges) improves data trust and usability**.
- **Scanner API helps detect sensitive data for governance and compliance**.
- **Data lineage tracking enhances visibility into data movement and transformations**.

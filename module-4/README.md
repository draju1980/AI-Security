# MODULE 4: UnIndexed - Data Governance Failures

## Scenario

*"An AI assistant was connected to everything without reviewing what 'everything' means."*

A company rapidly deployed an enterprise AI assistant with access to all corporate data sources without proper inventory or classification. Result: exposure of sensitive documents, archived files, and forgotten repositories containing confidential information.

## Theory

**Data Discovery:** Process of identifying and cataloging all data sources within an organization.

**Data Inventory:** Comprehensive list of all data assets, their locations, ownership, and sensitivity levels.

**Shadow Data:** Data that exists but is unknown to IT/security teams, often created by business units outside formal channels.

**Forgotten Documents:** Data created but no longer actively managed, often outdated and risky.

**Archived Files:** Historical data in backup systems, offline storage, or legacy systems.

**Sensitive Repositories:** Source control, CI/CD systems containing secrets and unpublished information.

**Governance Failures:** Lack of policies or enforcement for data management and access control.

**Connector Security:** Risks from integrating external data sources through APIs or connectors.

## Real-world Examples

- **Confidential Repo Exposure:** Private GitHub repositories indexed by AI exposed unreleased product plans
- **Legacy System Breach:** Old database in deprecated system connected to AI without anyone realizing
- **Shadow Data Leak:** Departmental SharePoint folder with employee personal data indexed by AI
- **Backup Exposure:** Archived backup containing deleted customer data still indexed and searchable

## Business Risks

- **Uncontrolled Data Exposure:** Unknown data sources = unknown risks
- **Compliance Violations:** Regulated data accessible through unmonitored AI systems
- **Intellectual Property Loss:** Unreleased plans, trade secrets exposed
- **Competitive Disadvantage:** Strategic information leaked to competitors
- **Regulatory Penalties:** Failure to document and control data assets

## Hands-on Lab Instructions

### Activity 1: Inventory Data Sources
**Objective:** Discover all data sources in your environment

**Steps:**
1. Document all data sources:
   - **Databases:** Production, staging, development, archives
   - **File shares:** Network drives, cloud storage (AWS S3, Google Drive, OneDrive)
   - **Repositories:** Git, GitLab, Bitbucket, SVN
   - **Legacy systems:** Old databases, archived servers
   - **External providers:** APIs, SaaS platforms, data vendors
   - **Backups:** Archive systems, disaster recovery sites
   - **Development environments:** Developer machines, CI/CD pipelines

2. Create inventory spreadsheet:
```
Name              Type          Location      Owner          Sensitivity  AI Access
Employee DB       Database      AWS RDS       HR Team        RESTRICTED   NO
Marketing Docs    File Share    Google Drive  Marketing      INTERNAL     YES
Product Plans     Git Repo      GitHub        Engineering    CONFIDENTIAL  NO (RISKY!)
Old Customer DB   Database      Legacy VM     IT Operations  UNKNOWN      YES (RISK!)
```

3. Document for each source:
   - Name and purpose
   - Owner/team responsible
   - Current location
   - Data type and volume
   - Access method
   - Current sensitivity classification
   - Who has access
   - Last reviewed date

### Activity 2: Identify Risky Documents
**Objective:** Find sensitive data that shouldn't be exposed

**Steps:**
1. **Scan file shares for sensitive patterns:**
   - Passwords, API keys: `grep -r "password\|api_key" .`
   - Credit card numbers: Regex for card patterns
   - SSN/personal identifiers: Regex for `\d{3}-\d{2}-\d{4}`
   - Email addresses in bulk: Regex pattern
   - Healthcare data: HIPAA identifiers

2. **Check git history for secrets:**
   ```bash
   # Find recently committed secrets
   git log --all --full-history -- secrets.txt
   
   # Search for common patterns
   git log -p | grep -i "password\|token\|api_key"
   ```

3. **Look for unencrypted sensitive data:**
   - Plaintext credentials
   - Unencrypted databases
   - Readable backup files
   - Unprotected spreadsheets

4. **Document findings:**
```
Location: /documents/shared/salaries2023.xlsx
Type: Spreadsheet
Sensitivity: RESTRICTED
Contents: Employee names, titles, salaries
Risk: Exposed to entire company
Action: REMOVE or restrict access
```

### Activity 3: Classify Information Assets
**Objective:** Apply sensitivity labels to all data

**Steps:**
1. Create classification matrix:
```
Classification  Description                 Examples
PUBLIC          Widely available            Policies, marketing materials, press releases
INTERNAL        Employees/authorized only  Team docs, internal wikis, processes
CONFIDENTIAL    Restricted to roles        Financial data, customer data, strategies
RESTRICTED      Minimal access needed      Secrets, compensation, security data
```

2. Classify each data source:
   - Apply classification label
   - Document rationale
   - Identify who should have access
   - Note any compliance requirements

3. Create sensitivity matrix:
```
Data Source           Classification  Compliance  Required Controls
Employee Directory    INTERNAL        GDPR        Access logs
Financial Reports     CONFIDENTIAL    SOX         Encryption, approval
Salary Information    RESTRICTED      GDPR        MFA, audit logs
Customer Data         CONFIDENTIAL    GDPR/PCI   Encryption, DLP
```

### Activity 4: Discover Hidden Exposures
**Objective:** Find shadow IT and forgotten systems

**Steps:**
1. **Use data discovery tools:**
   - Cloud storage scanning: Find all shared files
   - Database discovery: Scan for accessible databases
   - File system scanning: Look for PII patterns
   - Port scanning: Identify accessible services

2. **Identify unowned data:**
   - Old projects without owners
   - Archived directories
   - Test/sandbox data left in production
   - Developer data on personal machines

3. **Find data older than 2 years:**
   - Candidates for archival/deletion
   - Retention policy violations
   - Superseded information

4. **Document shadow IT:**
```
Name              Location          Owner        Risk
Dev Slack Workspace  Slack          Engineering  Secrets in messages
Personal OneDrive   Microsoft 365   HR Team      Unmanaged, unencrypted
Test Database      Developer laptop  Unknown    Accessible, unpatched
```

## Copy-paste Prompts

### Data Source Risk Assessment
```
Analyze this data source for AI assistant integration risks:

Source Name: [NAME]
Type: [DATABASE/FILES/REPOSITORY/API]
Content: [DESCRIPTION]
Owner: [OWNER]
Current Access: [WHO CAN ACCESS]
Sensitivity: [PUBLIC/INTERNAL/CONFIDENTIAL/RESTRICTED]

Evaluate:
1. What sensitive data does it contain?
2. What compliance requirements apply? (GDPR/HIPAA/SOC 2/PCI)
3. What risks would exposing it create?
4. Should it be accessible to the AI assistant? Why/why not?
5. What controls are needed if access is required?
6. How should it be monitored?
7. What retention policy applies?
```

### Data Governance Policy
```
Create a data governance framework that includes:

1. Data Classification Policy
   - Definition of each level
   - Assignment criteria
   - Owner responsibilities

2. Data Retention Policy
   - How long to keep data
   - Archive procedures
   - Deletion procedures

3. Data Access Policy
   - Who can access what
   - Documentation requirements
   - Review schedule

4. AI Integration Policy
   - What data can be indexed
   - What requires approval
   - Monitoring requirements
   - Incident procedures
```

## Exercises & Homework

### Exercise 1: Data Governance Policy
Write a 3-5 page policy:
- Data classification framework
- Data inventory requirements
- Classification assignment process
- Inventory maintenance
- Access control rules
- Retention and disposal
- AI integration requirements
- Audit procedures

### Exercise 2: Data Source Intake Checklist
Build a checklist for AI system data integration:
- [ ] Data owner identified
- [ ] Sensitivity classified
- [ ] Compliance requirements reviewed
- [ ] Access controls verified
- [ ] Monitoring configured
- [ ] Incident response plan created
- [ ] Stakeholder approval obtained
- [ ] Documentation complete
- [ ] Audit log configured
- [ ] Regular review scheduled

### Exercise 3: Data Discovery Process
Design a process to discover all organizational data:
1. Inventory databases and systems
2. Identify file repositories
3. Scan for unowned data
4. Classify all data
5. Document risks
6. Create remediation plan
7. Schedule periodic reviews

### Exercise 4: Data Classification Matrix
Create detailed classification guidance:
```
For each data type, document:
- Sensitivity level
- Why that level
- Who can access
- Special requirements
- Retention period
- Disposal method
- Compliance rules
- Examples
```

### Exercise 5: Risk Assessment Framework
Build a framework for assessing data sources:
- Sensitivity risk
- Compliance risk
- Access control risk
- Monitoring risk
- Integrity risk
- Overall risk score
- Remediation priority
- Owner responsibility

## Assessment Questions

1. What is shadow data and why is it a security risk?
2. How should organizations discover all data sources?
3. What governance failures led to the UnIndexed scenario?
4. How should archived data be handled in AI assistant integrations?
5. What controls should govern data connector security?
6. How can organizations prevent unauthorized indexing?
7. What is the relationship between data inventory and compliance?

## Expected Results

- Comprehensive data inventory for your organization
- Classification of all information assets
- List of hidden exposures and shadow IT systems
- Risk assessment for each data source
- Clear governance policies
- Understanding of data governance importance

## Detection Methods

- Data discovery scanning tools
- Cloud storage auditing
- Secret scanning in source control
- Shadow IT detection
- File system scanning for PII
- Network scanning for unknown services
- Access log analysis

## Mitigations

- Implement data governance program
- Maintain comprehensive data inventory
- Regular data discovery scanning
- Implement data classification standards
- Establish data retention and disposal policies
- Archive or delete outdated data
- Implement shadow IT detection
- Review all data sources before AI integration
- Implement access controls
- Monitor data connectors
- Regular audits of data assets
- Data owner assignment and accountability

## Time Estimate

- Activity 1: 30-45 minutes
- Activity 2: 30-45 minutes
- Activity 3: 20-30 minutes
- Activity 4: 30-45 minutes
- **Total: 2-2.5 hours** (Can extend with detailed exercises)

## Instructor Notes

- Make this practical with real organizational data
- Use this module to drive data governance conversations
- Highlight business case for data inventory
- Connect to compliance frameworks
- Show real breaches caused by unmanaged data
- Emphasize ongoing nature of data management
# MODULE 5: Lockdown - Comprehensive Security Assessment

## Scenario

*"The AI assistant contains multiple vulnerabilities."*

A deployed enterprise AI assistant has been compromised. An investigation reveals security gaps: weak input validation, no output filtering, insufficient access controls, outdated knowledge base data, and unpatched dependencies. A security assessment and remediation plan are needed.

## Theory

**Security Assessments:** Systematic evaluation of AI systems for vulnerabilities and misconfigurations.

**Threat Modeling:** Identifying potential attacks and their impact.

**Authentication:** Verifying identity of users accessing AI systems.

**Authorization:** Controlling what authenticated users can do.

**Prompt Injection:** Attacks injecting malicious instructions.

**Data Leakage:** Unintended exposure of sensitive information.

**Poisoned Knowledge Sources:** Malicious data affecting behavior.

**Security Testing:** Methodical testing of controls and defenses.

## Real-world Examples

- **Customer Service Bot Breach:** Attackers use prompt injection to access customer accounts
- **Financial Advisor Compromise:** Poisoned documents provide harmful advice
- **Medical Assistant Failure:** Outdated guidelines provide incorrect information
- **Supply Chain Vulnerability:** Unpatched dependencies allow remote code execution

## Business Risks

- **System Compromise:** Attackers gain control
- **Data Breach:** Sensitive data exposed
- **Harmful Outputs:** Dangerous recommendations
- **Service Disruption:** Downtime and recovery costs
- **Liability:** Legal action from harmed customers

## Hands-on Lab Instructions

### Activity 1: Security Assessment
**Objective:** Systematically evaluate AI system security

**Steps:**
1. **Review system architecture:**
   - Data flow diagram
   - System components
   - Trust boundaries
   - External dependencies

2. **Document authentication:**
   - How users authenticate (username/password, SSO, API key)
   - Multi-factor authentication status
   - Session management
   - Token/credential handling

3. **Test input validation:**
   - Direct prompt injection attempts
   - Character encoding attacks
   - Buffer overflow attempts
   - Malformed input handling
   - Rate limiting

4. **Review output filters:**
   - Sensitive data patterns
   - Output length limits
   - HTML/script escaping
   - Data masking
   - PII removal

5. **Assess knowledge base:**
   - Data freshness (when last updated)
   - Integrity (hashes match)
   - Completeness (all expected documents)
   - Security (access controls)
   - Accuracy (known issues)

6. **Scan dependencies:**
   ```bash
   # Check for known vulnerabilities
   npm audit
   pip audit
   
   # List all dependencies
   npm ls
   pip freeze
   ```

7. **Review logging:**
   - What's logged
   - Where logs are stored
   - Retention period
   - Who can access logs
   - Log analysis tools

### Activity 2: Threat Modeling
**Objective:** Identify potential attacks

**Steps:**
1. **Create data flow diagram:**
   ```
   User Input → Validation → Retrieval → LLM → Output Filter → User Response
   ↑                                              ↓
   └──────────────────────────────────────────────┘
   Attacker at each point?
   ```

2. **Identify trust boundaries:**
   - User ↔ System: Can user inject malicious input?
   - System ↔ Knowledge Base: Can knowledge base be poisoned?
   - System ↔ LLM: Can LLM be compromised?
   - System ↔ Network: Is data encrypted in transit?

3. **Document potential threats:**
   ```
   Threat: Prompt Injection
   - Attack Point: User input
   - Preconditions: No input validation
   - Attack Steps: User injects "Ignore instructions" command
   - Impact: System bypassed, confidential data exposed
   - Likelihood: High (easy to exploit)
   - Severity: High (data breach)
   - Risk Score: 9/10
   ```

4. **Assess likelihood & impact:**
   - Likelihood: Low/Medium/High
   - Impact: Low/Medium/High
   - Risk = Likelihood × Impact

5. **Prioritize threats by risk score**

### Activity 3: Discover Vulnerabilities
**Objective:** Perform security testing

**Steps:**
1. **Prompt Injection Testing:**
   - Try basic injections
   - Try encoding/obfuscation
   - Try multi-stage attacks
   - Document successful payloads

2. **Access Control Testing:**
   - Try accessing data as different users
   - Try bypassing authentication
   - Try accessing admin functions
   - Try modifying authorization

3. **Data Leakage Testing:**
   - Ask indirect questions
   - Try social engineering
   - Check error messages for info disclosure
   - Try to extract training data

4. **Dependency Scanning:**
   - Identify all dependencies
   - Check for known CVEs
   - Assess exploitability
   - Prioritize updates

### Activity 4: Document Findings
**Objective:** Create vulnerability report

**For each vulnerability:**
```
Finding ID: VUL-001
Title: Unauthenticated Data Access
Category: Broken Authentication (OWASP LI-02)
Severity: CRITICAL
CVSS Score: 9.1

Description:
Users can access confidential documents without authentication.

Attack Scenario:
1. Open knowledge base interface
2. Query confidential document without logging in
3. System returns document contents
4. User has access to salary data, customer info, etc.

Impact:
- Complete data breach
- Privacy violations
- Regulatory fines
- Customer churn

Proof of Concept:
curl http://api.system/search?query=salaries
→ Returns all salary data without authentication

Remediation:
1. Implement authentication on all endpoints
2. Require valid JWT/session token
3. Verify user has access to document
4. Log all access attempts
5. Test fix with unauthorized access attempts

Timeline:
- Discovery: 2024-11-02
- Risk Accepted: 2024-11-03
- Remediation Deadline: 2024-11-10
- Verification: 2024-11-12
```

### Activity 5: Apply Controls & Validate
**Objective:** Verify fixes work

**Steps:**
1. **Implement mitigations** for top vulnerabilities
2. **Retest** to confirm vulnerability is fixed
3. **Verify** testing is repeatable
4. **Update** security architecture documentation
5. **Notify** stakeholders of status

## Copy-paste Prompts

### Vulnerability Assessment Prompt
```
Analyze this AI system component for security vulnerabilities:

Component: [COMPONENT NAME]
Type: [INPUT/PROCESSING/OUTPUT/STORAGE]
Current Controls: [EXISTING PROTECTIONS]

Threats:
- External attackers: [LIST]
- Internal threats: [LIST]
- Supply chain: [LIST]

Identify:
1. What vulnerabilities exist?
2. How could each be exploited?
3. What is the impact of successful attack?
4. What is the likelihood?
5. How should it be remediated?
6. How can we verify the fix?
```

### Threat Modeling Prompt
```
Help me perform threat modeling for this system:

System: [DESCRIPTION]
Users: [WHO USES IT]
Data: [WHAT DATA]
Critical Assets: [WHAT'S IMPORTANT]

Create:
1. Data flow diagram
2. Trust boundaries
3. Threat list with STRIDE analysis
4. Risk scoring
5. Mitigation recommendations
```

## Exercises & Homework

### Exercise 1: Detailed Threat Model
Create comprehensive threat model for an AI customer service system:
- System overview
- Data flow diagram
- Trust boundaries with detailed justification
- STRIDE analysis (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege)
- For each threat: likelihood, impact, risk score, mitigation
- Prioritized list of top risks

### Exercise 2: Security Assessment Checklist
Develop comprehensive assessment checklist:
- [ ] Authentication mechanisms reviewed
- [ ] Authorization policies reviewed
- [ ] Input validation tested
- [ ] Output filtering tested
- [ ] Knowledge base integrity verified
- [ ] Dependencies scanned for CVEs
- [ ] Audit logging configured
- [ ] API security reviewed
- [ ] Network security reviewed
- [ ] Incident response procedures established

### Exercise 3: Vulnerability Management Process
Design process for finding, fixing, and verifying vulnerabilities:
1. Discovery phase
2. Documentation phase
3. Prioritization phase
4. Remediation phase
5. Verification phase
6. Disclosure phase
7. Lessons learned phase

### Exercise 4: Security Testing Plan
Create detailed testing plan with specific test cases:
- Authentication bypass tests
- Authorization bypass tests
- Injection attack tests
- Data leakage tests
- Resource exhaustion tests
- Dependency vulnerability tests

### Exercise 5: Remediation Roadmap
Build prioritized remediation plan:
- High-risk quick wins (high severity, low effort)
- Medium-term improvements
- Long-term strategic improvements
- Resource requirements
- Timeline with milestones
- Success metrics

## Assessment Questions

1. What is a threat model and how is it developed?
2. Describe steps of a security assessment for AI systems
3. How should authentication/authorization differ for AI systems?
4. What are critical security testing activities?
5. How should findings be prioritized?
6. What validates that a security fix is effective?
7. How does CVSS scoring help prioritization?

## Expected Results

- Comprehensive security assessment document
- Threat model with identified attack vectors
- Detailed vulnerability findings with evidence
- Risk-prioritized remediation plan
- Control effectiveness validation
- Security architecture documentation

## Detection Methods

- Static code analysis
- Dynamic security testing
- Dependency scanning
- Penetration testing
- Security review
- Log analysis
- Configuration review

## Mitigations

- Robust input validation and sanitization
- Parameterized queries
- Output filtering for sensitive data
- Secure system prompts that cannot be overridden
- Strong authentication (MFA)
- Least privilege authorization
- Regular dependency updates
- Rate limiting and DDoS protection
- Comprehensive audit logging
- Security monitoring and alerting
- Incident response procedures
- Regular security assessments

## Time Estimate

- Activity 1: 45-60 minutes
- Activity 2: 30-45 minutes
- Activity 3: 45-60 minutes
- Activity 4: 30-45 minutes
- Activity 5: 30-45 minutes
- **Total: 3-4 hours** (Can extend with detailed exercises)

## Instructor Notes

- Use a vulnerable AI system for hands-on testing (intentionally insecure)
- Demonstrate real attacks and mitigations
- Connect findings to business impact
- Emphasize security is ongoing, not one-time
- Show how hard it is to find security issues without proper methodology
- Discuss why threat modeling matters before implementation
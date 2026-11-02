# MODULE 7: OWASP Top 10 for LLM Applications

## Theory

The OWASP Top 10 for LLM Applications identifies the most critical security risks for LLM-based systems:

### LI-01: Prompt Injection
Direct injection of malicious instructions into prompts to override system behavior or extract sensitive information.

### LI-02: Sensitive Information Disclosure
LLMs unintentionally expose training data, secrets, or user information in responses.

### LI-03: Supply Chain Vulnerabilities
Third-party data, models, or APIs introduce vulnerabilities into AI systems.

### LI-04: Data Poisoning
Malicious data in training sets or knowledge bases corrupts model behavior.

### LI-05: Excessive Agency
AI agents have too many capabilities or too much autonomy, enabling harmful actions.

### LI-06: Model Denial of Service
Attackers consume resources to degrade or disable AI services.

### LI-07: System Prompt Leakage
System prompts containing sensitive instructions are exposed to users.

### LI-08: Vector and Embedding Attacks
Attacks targeting embedding vectors or vector databases.

### LI-09: Misinformation and Reputational Damage
AI systems generate false information causing reputational harm.

### LI-10: Unbounded Consumption of Resources
AI systems consume excessive compute resources due to malicious input or bugs.

## Real-world Examples

- **LI-01:** SQL injection-style attack on prompts
- **LI-02:** Training data or secrets exposed in responses
- **LI-03:** Compromised dependency in AI pipeline
- **LI-04:** Malicious training samples change model behavior
- **LI-05:** AI agent deletes files without proper controls
- **LI-06:** Repeated API calls exhaust rate limits
- **LI-07:** "DAN" jailbreak exposes internal instructions
- **LI-08:** Poisoned embeddings manipulate retrieval

## Business Risks

- Each vulnerability type: Specific business consequences
- Cumulative risk: Multiple vulnerabilities create attack chains
- Compliance impact: OWASP findings contribute to violations
- Reputational risk: Public knowledge of vulnerabilities damages trust

## Hands-on Lab Instructions

### Activity 1: Map Vulnerabilities to Your Systems
For each OWASP LI-01 through LI-10, identify:
- How it manifests in your AI systems
- Specific attack scenarios
- Potential impact
- Current controls (if any)
- Risk level (Low/Medium/High)

Create vulnerability matrix for your systems.

### Activity 2: Test Controls
For each vulnerability, test whether current controls prevent it:
- Document test results and any bypasses discovered
- Estimate control effectiveness
- Identify gaps

### Activity 3: Review Mitigations
For each OWASP vulnerability, document:
- Recommended mitigations (from OWASP)
- Which mitigations are implemented
- Gaps and needed improvements
- Create prioritized remediation roadmap

## OWASP Mitigations Summary

**LI-01 Prompt Injection:** Input validation, parameterization, sandboxing, system prompts

**LI-02 Information Disclosure:** Output filtering, data classification, access controls

**LI-03 Supply Chain:** Vendor assessment, dependency scanning, SBOMs

**LI-04 Data Poisoning:** Data validation, integrity checks, monitoring

**LI-05 Excessive Agency:** Least privilege, tool restrictions, approval workflows

**LI-06 Model DoS:** Rate limiting, resource quotas, authentication

**LI-07 System Prompt Leakage:** Prompt hardening, jailbreak testing, monitoring

**LI-08 Vector Attacks:** Vector validation, poisoning detection, monitoring

**LI-09 Misinformation:** Fact-checking, output validation, confidence scoring

**LI-10 Resource Consumption:** Rate limiting, timeout protection, resource quotas

## Copy-paste Prompts

### OWASP Assessment Prompt
```
Assess your AI system against OWASP LLM Top 10:

For each vulnerability (LI-01 through LI-10):
1. Is your system vulnerable to this attack?
2. What evidence do you have?
3. What controls currently mitigate it?
4. How could an attacker exploit it?
5. What is the business impact?
6. What remediation is needed?

Create a prioritized list of needed improvements.
```

## Exercises & Homework

### Exercise 1: OWASP Assessment
Detailed assessment of your organization's AI systems against each OWASP LLM vulnerability:
- For each: vulnerable? How? Impact? Controls? Fix?
- Prioritized list of remediations
- Timeline and owner for each

### Exercise 2: Mitigation Design
For your top 3 vulnerabilities, design detailed mitigations:
- What specifically will be implemented
- Why it will work
- How to verify it works
- Timeline
- Resource requirements

### Exercise 3: Security Test Cases
Build security test cases for each OWASP vulnerability:
- Test input
- Expected outcome
- Pass/fail criteria
- Evidence of success

### Exercise 4: Remediation Roadmap
Create remediation roadmap with:
- Quick wins (high severity, low effort)
- Medium-term improvements
- Long-term strategic improvements
- Resource requirements
- Timeline with milestones

### Exercise 5: OWASP Training Content
Develop training materials for your team on OWASP LLM Top 10:
- Overview presentation
- Detailed scenarios for each vulnerability
- Examples from your systems
- How to avoid them in development
- Who to contact for questions

## Assessment Questions

1. Explain the relationship between OWASP Top 10 Web and OWASP LLM Top 10
2. How does prompt injection differ from traditional SQL injection?
3. What is excessive agency and why is it a unique risk?
4. How should supply chain vulnerabilities be managed?
5. Why is system prompt leakage a unique risk for LLMs?
6. How should organizations prioritize OWASP vulnerabilities?
7. Which OWASP vulnerabilities are most relevant to your organization?

## Expected Results

- Understanding of each OWASP LLM vulnerability
- Vulnerability mapping for your systems
- Assessment of control effectiveness
- Prioritized remediation roadmap
- Team awareness of OWASP framework

## Detection Methods

- Security testing for OWASP vulnerabilities
- Log analysis for injection attempts
- Monitoring for data exfiltration
- Dependency scanning
- Data integrity monitoring
- Resource usage monitoring

## Time Estimate: 2-3 hours

## Instructor Notes

- OWASP is the gold standard—all organizations should use this framework
- Review official OWASP LLM Top 10 document
- Show how OWASP provides specific mitigations
- Connect to existing security practices
- Use OWASP as framework for entire course

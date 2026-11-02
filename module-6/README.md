# MODULE 6: AI Security Monitoring and Defense

## Theory

**AI Logging:** Recording all AI interactions, prompts, responses, and system actions for audit and analysis.

**Detection Strategies:** Methods for identifying attacks, anomalies, and security incidents in real-time.

**Audit Trails:** Immutable records of who did what, when, and what the result was.

**Security Monitoring:** Continuous observation of AI system behavior for security indicators.

**Anomaly Detection:** Using ML/statistics to identify unusual patterns deviating from normal behavior.

**AI Incident Response:** Procedures for detecting, containing, and remediating AI-specific incidents.

**AI Governance:** Policies and processes for managing AI systems responsibly.

**Security Policies:** Documented rules governing AI system use and security requirements.

## Real-world Examples

- **Attack Detection:** Monitoring detects repeated prompt injection attempts indicating targeted attack
- **Data Exfiltration:** Logging reveals suspicious data access patterns enabling rapid response
- **Model Drift:** Monitoring detects quality degradation indicating potential poisoning
- **Insider Threat:** Audit logs identify employee inappropriately accessing restricted knowledge

## Business Risks

- **Undetected Breaches:** Without monitoring, attacks go unnoticed until major damage occurs
- **Compliance Failures:** Lack of logging violates regulatory requirements
- **Slow Response:** Without detection, incident response time increases dramatically
- **Evidence Loss:** No logs means no forensic evidence for investigation
- **Regulatory Penalties:** Failure to implement required monitoring and logging

## Hands-on Lab Instructions

### Activity 1: Implement Comprehensive Logging
1. Set up centralized log aggregation (ELK, Splunk, Cloud Logging)
2. Configure logging for:
   - All user interactions with timestamps
   - All prompts sent to LLM
   - All responses generated
   - All data access and retrieval
   - All authentication events
   - All authorization failures
   - System errors and exceptions
3. Ensure logs are immutable (cannot be deleted)
4. Implement log retention policy (1-3 years typically)
5. Define log rotation strategy

### Activity 2: Create Monitoring Dashboards
1. Build real-time monitoring dashboard showing:
   - Request volume and trends
   - Error rates and types
   - Authentication failures
   - Unusual query patterns
   - Data access distribution
   - Response times
   - Resource utilization
2. Create alerts for:
   - Failed authentication attempts (>5 in 10 min)
   - Injection attack indicators
   - Unauthorized data access
   - Service degradation
   - Resource exhaustion
3. Implement escalation procedures (who gets alerted when)

### Activity 3: Design Detection Strategies
1. Identify indicators of compromise (IoCs) for AI systems:
   - Repeated special characters in prompts
   - Known injection keywords
   - Unusual query patterns
   - Rapid successive requests
   - Requests for non-existent resources
   - Responses containing suspicious patterns
2. Define detection rules for:
   - Prompt injection attempts (string patterns)
   - Data exfiltration (sensitive data in responses)
   - Anomalous access (user accessing outside normal scope)
   - DoS attacks (excessive requests)
3. Implement using rule engines and machine learning

### Activity 4: Build Response Procedures
1. Create incident response runbooks for:
   - Prompt injection attack detected
   - Unauthorized data access detected
   - Data exfiltration in progress
   - System unavailability
   - Knowledge base integrity failure
2. Define escalation procedures
3. Create communication templates
4. Define evidence preservation requirements

## Copy-paste Prompts

### Monitoring Alert Design
```
Design a monitoring alert for this threat:

Threat: [DESCRIBE ATTACK/ANOMALY]
Indicators: [WHAT WOULD WE SEE IN LOGS?]
False Positive Rate: [ESTIMATE]
Response Time Needed: [e.g., immediate, 1 hour]
Difficulty to Detect: [Low/Medium/High]

Define:
1. Alert condition (what triggers alert)
2. Alert severity level
3. Who should be notified
4. Initial response steps
5. Escalation path
6. How to verify if real vs. false positive
```

## Exercises & Homework

### Exercise 1: Logging Strategy
Design comprehensive logging framework:
- What to log
- Where to log
- How to store logs
- Log retention period
- Who can access logs
- Log review procedures

### Exercise 2: Monitoring Dashboard Spec
Specify real-time monitoring dashboard:
- What metrics to display
- What thresholds trigger alerts
- Who is responsible for monitoring
- Escalation procedures
- Daily/weekly reviews

### Exercise 3: Detection Rules
Develop 10 specific detection rules:
```
Rule 1: Prompt Injection Detection
Condition: Request contains ["ignore", "overrid", "instruction"]
Severity: HIGH
Response: Flag for review, don't execute

Rule 2: Rapid Request Detection
Condition: >100 requests per minute from single user
Severity: MEDIUM
Response: Rate limit user, notify security team
```

### Exercise 4: Incident Response Plan
Write detailed response procedures for 3 scenarios:
1. Prompt injection detected
2. Unauthorized data access
3. Service unavailability

### Exercise 5: Security Policy Document
Create AI security policy covering:
- Acceptable use
- Data handling
- Incident procedures
- Compliance requirements
- User responsibilities

## Assessment Questions

1. What should be logged for each AI interaction?
2. How can anomalies be detected in behavior?
3. What compliance requirements mandate AI logging?
4. Describe indicators of compromise for injection attacks
5. What is the purpose of audit trails?
6. How do incident response procedures differ for AI incidents?
7. What metrics indicate system health?

## Expected Results

- Comprehensive logging infrastructure
- Real-time monitoring dashboards
- Incident detection capabilities
- Response procedures and runbooks
- Audit trail for compliance
- Monitoring and alerting operational

## Time Estimate: 2-3 hours

## Instructor Notes

- Demonstrate real attack logs and detection
- Show how monitoring saved organizations
- Emphasize detection is first step of response
- Connect to compliance requirements

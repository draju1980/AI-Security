# MODULE 8: Capstone Project - Secure Enterprise AI Assistant

## Project Overview

Design and secure an enterprise AI assistant using your chosen platform. Perform a comprehensive security assessment, threat modeling, and develop a complete remediation plan.

## Platform Options

**Hosted Solutions:**
- ChatGPT / GPT-4
- Claude (Anthropic)
- Gemini (Google)
- Copilot (Microsoft)

**Self-Hosted:**
- Ollama
- OpenWebUI
- AnythingLLM
- LlamaIndex

**Hybrid:**
- Combination of hosted and local components

## Project Requirements

### 1. Threat Model
- Data flow diagram
- Trust boundary identification
- Threat enumeration
- Risk assessment (likelihood × impact)
- Prioritization by risk score

### 2. Trust Boundary Analysis
- Identify all trust boundaries
- Data crossing each boundary
- Security controls at each boundary
- Assessment of boundary strength
- Recommendations for improvement

### 3. Prompt Injection Assessment
- Test against direct injection attacks
- Test against indirect injection from documents
- Test context window attacks
- Document findings and exploitability
- Estimate impact and likelihood

### 4. Data Poisoning Assessment
- Identify knowledge base integrity controls
- Test document validation
- Assess access controls on knowledge base
- Evaluate supply chain security
- Rate risk level

### 5. Sensitive Information Disclosure Assessment
- Identify sensitive data sources
- Test access controls
- Attempt data extraction through prompting
- Assess information leakage risk
- Rate risk level

### 6. Security Review
- Authentication and authorization assessment
- Input validation review
- Output filtering assessment
- Logging and monitoring review
- Dependency vulnerability scan
- API security assessment
- Rate each as: Adequate / Needs Improvement / Critical Gap

### 7. Mitigation Plan
- For each finding, specify remediation
- Prioritize by severity and effort
- Estimate implementation timeline
- Identify resource requirements
- Define success criteria

### 8. Executive Summary
- 1-2 page overview of findings
- Risk level assessment (Low/Medium/High/Critical)
- Key recommendations
- Business impact statement
- Estimated remediation cost and timeline

## Deliverables

### 1. Security Assessment Report
**Contents:**
- Executive summary (1-2 pages)
- System architecture and data flow
- Threat model (with diagrams)
- Detailed vulnerability findings organized by OWASP category
- Evidence and proof of concept for each finding
- Risk scoring and prioritization
- Appendices (screenshots, test results, logs, etc.)

**Format:** PDF or Markdown, 15-25 pages typical

### 2. Risk Register
**Spreadsheet with columns:**
- ID (e.g., R-001)
- Title
- Description
- Vulnerability Category (OWASP LI-XX)
- Likelihood (Low/Medium/High)
- Impact (Low/Medium/High)
- Risk Score (Likelihood × Impact, typically 1-9)
- Current Controls
- Recommended Mitigation
- Timeline to remediate
- Owner/responsible party
- Status (Open/In Progress/Remediated)

### 3. Remediation Plan
**Detailed action plan:**
- Prioritized list of remediations
- For each remediation:
  - Risk being mitigated
  - Mitigation description
  - Implementation steps
  - Resource requirements (time, people, tools)
  - Timeline/deadline
  - Success criteria
  - Owner/responsible party
  - Dependencies on other items
- Phase schedule:
  - Quick wins (high severity, low effort)
  - Medium-term improvements
  - Long-term strategic improvements

### 4. Final Presentation
**20-30 minute presentation:**
- System overview (5 min)
- Threat model summary (5 min)
- Critical findings and impact (10 min)
- Recommended remediation roadmap (5 min)
- Q&A (5 min)

## Project Timeline

### Week 1: System Selection and Setup
- Choose AI platform
- Deploy or configure system
- Create sample knowledge base
- Set up test users and roles

### Week 2: Threat Modeling
- Create system architecture diagram
- Draw detailed data flow
- Identify trust boundaries
- Enumerate potential threats
- Assess likelihood and impact
- Document threat model

### Week 3: Security Testing
- Perform prompt injection testing
- Test access control enforcement
- Attempt data leakage extraction
- Scan dependencies for CVEs
- Test authentication/authorization
- Document all findings with evidence

### Week 4: Assessment and Planning
- Score each finding by likelihood and impact
- Create risk register
- Present findings to stakeholder group
- Get agreement on prioritization
- For each finding, design mitigation
- Create remediation roadmap
- Write comprehensive report
- Prepare presentation

## Assessment Criteria

| Criterion | Excellent (A) | Good (B) | Adequate (C) | Poor (F) |
|-----------|---------------|---------|------------|---------|
| Threat Model | Comprehensive, clear data flows, all boundaries | Good coverage, minor gaps | Basic model, some missing | Incomplete |
| Vulnerability Findings | Multiple findings across categories, well documented | Good set, well documented | Adequate findings, some lack detail | Few findings |
| Risk Assessment | Accurate scoring, clear justification | Good scoring, sound justification | Reasonable, some gaps | Weak or missing |
| Remediation Plan | Practical, prioritized, resourced, achievable | Good plan, minor gaps | Basic plan, lacks detail | Vague or impractical |
| Presentation | Clear, professional, structured, strong Q&A | Good presentation | Adequate, some clarity issues | Weak organization |

**Grading Weight:**
- Threat Model: 20%
- Vulnerability Assessment: 25%
- Risk Assessment: 20%
- Remediation Plan: 20%
- Report & Presentation: 15%

## Required Outputs

1. **Written Report (PDF):** 15-25 pages
2. **Risk Register (Excel):** All findings documented
3. **Remediation Plan (Excel or Markdown):** Prioritized actions
4. **Presentation (PowerPoint or Slides):** 20-30 minutes
5. **Supporting Files:**
   - Threat model diagrams
   - Screenshots of vulnerabilities
   - Test results and evidence
   - System architecture diagrams

## Copy-paste Templates

### Threat Model Template
```markdown
## Threat Model: [System Name]

### System Overview
[Description]

### Data Flow Diagram
[ASCII or graphical representation]

### Trust Boundaries
- Boundary 1: [Description]
- Boundary 2: [Description]

### Threat Enumeration
| Threat | Boundary | Likelihood | Impact | Risk Score | Mitigation |
|--------|----------|-----------|--------|-----------|-----------|
| Prompt Injection | User Input | High | High | 9 | Input validation |
```

### Risk Register Template
```csv
ID,Title,Category,Likelihood,Impact,Score,Controls,Mitigation,Timeline,Owner,Status
R-001,Prompt Injection,LI-01,High,High,9,None,Parameter validation,2024-11-30,Security Lead,Open
```

## Success Indicators

Students have successfully completed capstone when they can:

1. Create comprehensive threat models for AI systems
2. Identify and test for real vulnerabilities
3. Assess risk accurately and prioritize appropriately
4. Design practical, implementable mitigations
5. Communicate findings clearly to audiences
6. Understand business context of AI security decisions
7. Follow professional security assessment practices

## Resources

- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [NIST AI Risk Management Framework](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)
- [OpenAI Security Best Practices](https://platform.openai.com/docs/guides/safety-best-practices)

## Instructor Notes

### Capstone Duration
- 2-3 weeks of part-time work
- 1 week full-time intensive
- Team-based (3-4 people) projects expand scope

### Supporting Activities
- Invite security professionals to review presentations
- Consider industry-specific variations:
  - Healthcare AI (HIPAA focus)
  - Financial AI (SEC focus)
  - Legal AI (attorney ethics focus)
- Share exemplar project from previous cohort
- Provide rubric and grading guidelines

### Grading Recommendations
- Grade on depth, rigor, and practicality more than finding volume
- Fewer high-quality findings beat numerous shallow ones
- Strong risk prioritization is more important than finding everything
- Realistic remediation plans are critical
- Professional communication is expected

### Common Issues
- **Too many trivial findings:** Guide toward impact assessment
- **No risk prioritization:** Emphasize likelihood × impact scoring
- **Unrealistic remediation:** Discuss effort/timeline estimation
- **Poor documentation:** Require clear, professional reports
- **Weak threat modeling:** Spend time on data flows and boundaries

## Final Project Checklist

- [ ] System fully documented (architecture, data flow)
- [ ] Threat model complete with clear data flows
- [ ] All trust boundaries identified and justified
- [ ] Security testing performed and documented
- [ ] Findings include evidence and proof of concept
- [ ] Risk scoring applied consistently
- [ ] Remediation plan is practical and realistic
- [ ] Timeline accounts for resource constraints
- [ ] Presentation is clear and professional
- [ ] All deliverables submitted on time
- [ ] Report is well-organized and easy to follow
- [ ] Recommendations align with findings

## Time Estimate

- System setup: 5-10 hours
- Threat modeling: 10-15 hours
- Security testing: 15-20 hours
- Assessment and planning: 10-15 hours
- Report writing: 10-15 hours
- Presentation preparation: 5-10 hours
- **Total: 55-85 hours** (varies by group size and platform choice)

## Success Examples

Strong capstone projects typically feature:
- Clear, professional documentation
- Realistic threat models based on architecture
- Multiple findings across OWASP categories
- Accurate risk assessment with clear justification
- Practical remediation plan with timelines
- Strong understanding of trade-offs and priorities
- Clear communication to both technical and non-technical audiences

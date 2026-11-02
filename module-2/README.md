# MODULE 2: Data Poisoning in RAG Systems

## Theory

**What is Data Poisoning?** Introducing false or malicious data into training sets or knowledge bases to corrupt model outputs or behavior. A critical supply chain vulnerability.

**Knowledge Base Poisoning:** Inserting false documents into RAG systems to influence recommendations and advice without detection.

**Document Manipulation:** Modifying legitimate documents in knowledge bases to change AI responses and introduce bias or misinformation.

**Embedding Manipulation:** Crafting documents with specific word choices to appear relevant in embedding space when they contain malicious content.

**Vector Database Risks:** Compromised write access enables injection of malicious vectors that appear similar to legitimate queries.

**AI Supply Chain Security:** Risks from third-party datasets, pre-trained models, APIs, and data providers used in AI systems.

**Trust Verification:** Validating data sources and document authenticity before inclusion in knowledge bases.

**Document Integrity:** Ensuring documents haven't been modified through hashing, digital signatures, or versioning.

## Real-world Examples

- **Wikipedia Poisoning:** Attacker modifies Wikipedia articles used as knowledge base, affecting financial advice AI → Investment recommendations based on false data
- **Academic Database Compromise:** Malicious research papers uploaded to academic knowledge base influence medical AI recommendations → Doctors use poisoned guidelines
- **Product Review Injection:** False reviews inserted into e-commerce AI recommendation system → Users buy products based on fabricated reviews
- **Supply Chain Attack:** Third-party data provider compromised, poisoning multiple AI systems → Widespread impact across customers

## Business Risks

- **Recommendation Quality:** Poisoned AI gives harmful recommendations (medical, financial, legal advice)
- **Regulatory Violations:** Non-compliant advice due to poisoned knowledge base violates healthcare/financial regulations
- **Customer Harm:** Users receive wrong information causing financial, health, or safety damage
- **Loss of Trust:** Customers lose confidence in AI system after discovering poisoning
- **Legal Liability:** Litigation over damages caused by poisoned recommendations
- **Business Interruption:** Need to shut down and clean systems

## Hands-on Lab Instructions

### Activity 1: Create Trusted Documents (Baseline)
**Objective:** Establish clean baseline and verify integrity

**Steps:**
1. Create a set of 20 baseline documents representing clean knowledge:
   ```
   doc1.txt - Company vacation policy (2023)
   doc2.txt - Remote work guidelines
   doc3.txt - Benefits overview
   ... (20 total)
   ```

2. Calculate SHA-256 hash of each document:
   ```bash
   sha256sum doc1.txt > hashes.txt
   sha256sum doc2.txt >> hashes.txt
   # Continue for all 20
   ```

3. Store hashes in secure, immutable location
4. Test that knowledge base returns correct, consistent information
5. Document baseline accuracy metrics:
   - Questions answered correctly: X/20
   - Average response length
   - Confidence scores

### Activity 2: Create Poisoned Documents
**Objective:** Demonstrate how attackers modify documents

**Steps:**
1. **Subtle Modification (5 documents):**
   - Modify vacation policy: "15 days" → "5 days"
   - Change remote work: "3 days/week" → "1 day/week"
   - Adjust benefits percentages downward
   - Add contradictory statements
   - Modify compliance requirements

2. **Plausible False Documents (3 documents):**
   - Create realistic-looking policy updates with wrong dates
   - Add "updated" markers and version numbers
   - Use official-sounding language
   - Include subtle errors that seem intentional

3. **Entirely False Documents (2 documents):**
   - Create completely fabricated policies
   - Make them appear authoritative
   - Include references and approvals

4. **Add to knowledge base** and document:
   - Insertion method (direct upload, API, database access)
   - Timestamp of injection
   - Whether audit logging captured it

### Activity 3: Compare Outputs Before/After Poisoning
**Objective:** Measure impact of poisoning on AI behavior

**Test Queries:**
```
1. "What is our vacation policy?"
2. "How many days can I work remotely?"
3. "What benefits do employees get?"
4. "What is the salary review process?"
5. "How do we handle data privacy?"
```

**For each query, document before and after:**

| Metric | Before | After | Difference |
|--------|--------|-------|-----------|
| Response accuracy | | | |
| Recommendations given | | | |
| Confidence score | | | |
| Retrieved documents | | | |
| Document ranking | | | |

**Analysis:**
- How much did poisoning affect responses?
- Would user notice the changes?
- What type of poison is most effective?

### Activity 4: Observe Retrieval Drift
**Objective:** Monitor how poisoned documents influence ranking over time

**Steps:**
1. Track which documents are retrieved for standard queries over 5 days
2. Introduce poisoned document on day 2
3. Monitor if poisoned document starts appearing in results
4. Check if retrieval rankings shift toward poisoned content
5. Analyze retrieval scores:

```
Day 1 (Clean):
  Query: "vacation policy"
  - doc1.txt (score: 0.95)
  - doc8.txt (score: 0.87)
  - doc12.txt (score: 0.76)

Day 3 (Poisoned):
  Query: "vacation policy"
  - poisoned_doc.txt (score: 0.98) ← Higher rank!
  - doc1.txt (score: 0.92)
  - doc8.txt (score: 0.84)
```

**Key Questions:**
- Did poisoned document become top result?
- Did original documents drop in ranking?
- What embeddings strategy made poison effective?

## Copy-paste Prompts

### Document Validation Prompt
```
You are a document quality checker for a knowledge base. Analyze this document 
and report:

1. Claims that contradict reliable sources
2. Missing citations for factual claims
3. Suspicious modifications or formatting issues
4. Red flags indicating malicious intent
5. Inconsistencies with other documents
6. Outdated information
7. Unauthorized changes from version history

Document: [INSERT DOCUMENT]

Also suggest: Is this document safe to include in the knowledge base?
```

### Integrity Verification Prompt
```
I'm performing data integrity checks on documents. For this set:

Document 1 hash: abc123...
Document 2 hash: def456...
Document 3 hash: ghi789...

Current hashes:
Document 1: abc123... ✓
Document 2: xyz999... ✗ (MISMATCH!)
Document 3: ghi789... ✓

What could cause Document 2's hash to change?
How should we investigate this potential tampering?
```

## Exercises & Homework

### Exercise 1: Data Governance Policy
Write a 2-page policy for knowledge base management:
- Approval process for new documents
- Change control procedures
- Version management
- Audit logging requirements
- Incident response plan
- Supplier/third-party vetting

### Exercise 2: Integrity Verification Script
Create a Python script that:
```python
# Pseudocode
def verify_document_integrity(doc_path, stored_hash):
    current_hash = calculate_sha256(doc_path)
    if current_hash != stored_hash:
        alert("TAMPERING DETECTED!")
        log_incident()
    return current_hash == stored_hash

# Run periodic checks
for doc in knowledge_base:
    verify_document_integrity(doc.path, doc.trusted_hash)
```

### Exercise 3: Document Validation Checklist
Create a checklist for evaluating documents before inclusion:
- [ ] Source is trustworthy
- [ ] Document is recent (< 1 year)
- [ ] All claims are cited
- [ ] No contradictions detected
- [ ] No suspicious formatting
- [ ] Digital signature valid
- [ ] Author/approver verified
- [ ] Compliance review complete
- [ ] Hash stored securely
- [ ] Change log updated

### Exercise 4: Change Control Process
Design a change control workflow:
```
Document Update Request
  ↓
Review: Is change legitimate?
  ↓
Approval: Multiple reviewers needed
  ↓
Staging: Test in sandbox environment
  ↓
Comparison: Show before/after
  ↓
Approval: Final sign-off
  ↓
Deployment: Update knowledge base
  ↓
Verification: Check integrity hashes
  ↓
Logging: Record all changes
```

### Exercise 5: Supplier Security Assessment
Create a questionnaire for third-party data providers:
1. What security controls do you have?
2. How do you verify data authenticity?
3. What audit logs do you maintain?
4. Can you sign data with digital signatures?
5. What's your incident response process?
6. Do you test for data poisoning?
7. Can you provide SBOMs (Software Bill of Materials)?
8. What compliance certifications do you have?

## Assessment Questions

1. Explain the difference between training data poisoning and knowledge base poisoning
2. How can attackers make poisoned documents appear legitimate?
3. What are the consequences of embedding manipulation in RAG systems?
4. Describe a supply chain attack on an AI system with specific steps
5. What controls would prevent unauthorized knowledge base modifications?
6. How can organizations verify the integrity of third-party datasets?
7. What is the relationship between data poisoning and OWASP vulnerabilities?

## Expected Results

- Observable changes in AI responses after poisoning
- Clear before/after comparison demonstrating impact
- Understanding of poisoning attack vectors
- Recognition of importance of document integrity
- Awareness of supply chain risks

## Detection Methods

- Document hashing: Compare current hashes against known-good values
- Source verification: Check document provenance and authorship
- Content analysis: Use ML to detect anomalous or suspicious documents
- Statistical analysis: Monitor embedding distributions for outliers
- Version control: Track all changes to knowledge base with audit logs
- Integrity monitoring: Alert on unauthorized modifications
- Comparison checks: New documents compared to existing knowledge

## Mitigations

- Implement strict access controls on knowledge base modifications
- Use digital signatures for document authenticity
- Maintain audit logs of all document changes with timestamps
- Implement document versioning with immutable history
- Perform regular integrity checks using cryptographic hashing
- Validate data sources before inclusion
- Implement change approval workflows with multiple reviewers
- Use sandboxed evaluation of new documents before production
- Implement anomaly detection on retrieved documents
- Regular security assessments of data pipeline
- Vendor security assessments and SLAs
- Rate limiting on document uploads

## Time Estimate

- Activity 1: 20-30 minutes
- Activity 2: 30-40 minutes
- Activity 3: 30-40 minutes
- Activity 4: 20-30 minutes
- **Total: 2-3 hours**

## Instructor Notes

- Make the impact of poisoning visible through side-by-side comparisons
- Show real examples of data poisoning in public datasets
- Discuss realistic attack scenarios in the students' industry
- Emphasize that data governance is a business problem, not just IT
- Connect to supply chain security initiatives
- Show how difficult poisoning is to detect without proper controls
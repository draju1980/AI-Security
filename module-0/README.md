# MODULE 0: Introduction to AI Security

## Theory

### What is AI?
Artificial Intelligence refers to computer systems designed to perform tasks that typically require human intelligence. These include learning from data, recognizing patterns, understanding language, and making decisions.

### What is Generative AI?
Generative AI models can create new content—text, images, code, audio—based on patterns learned from training data. Unlike traditional AI that classifies or predicts, generative AI produces novel outputs.

### What is an LLM?
A Large Language Model (LLM) is a neural network trained on massive amounts of text data to understand and generate human language. Examples: GPT-4, Claude, Gemini, Llama.

### What is Prompt Engineering?
Prompt engineering is the practice of crafting input text (prompts) to guide AI models toward desired outputs. It includes techniques like zero-shot, few-shot learning, chain-of-thought, and role-based prompting.

### What is RAG?
Retrieval-Augmented Generation (RAG) combines LLMs with external knowledge sources. The system retrieves relevant documents and feeds them to the LLM to generate responses based on current, accurate information.

### What are AI Agents?
AI agents are autonomous systems that can take actions, use tools, plan sequences of steps, and interact with their environment to achieve goals. They combine reasoning with tool use.

### What are Embeddings?
Embeddings convert text, images, or other data into numerical vectors that capture semantic meaning. These allow AI systems to understand similarity and relationships between content.

### What are Vector Databases?
Vector databases store and search through embedding vectors efficiently. They enable fast similarity search, essential for RAG systems to retrieve relevant documents.

### AI Security Fundamentals
AI security involves protecting AI systems from attacks, ensuring data privacy, maintaining system integrity, and managing risks throughout the AI lifecycle.

### AI Threat Landscape
Threats include prompt injection, data poisoning, model theft, privacy violations, supply chain attacks, and misuse of AI capabilities.

### OWASP Top 10 for LLM Applications
The industry framework identifying the most critical security risks in LLM applications.

### AI Security Lifecycle
Security spans development, deployment, monitoring, and incident response phases.

## Real-world Examples

- **Prompt Injection Attack:** Attacker modifies system behavior by injecting malicious instructions into user input
- **Data Leakage:** AI system inadvertently reveals sensitive information from training data or knowledge bases
- **Model Hallucination:** AI generates false but plausible information not in its training data
- **Supply Chain Compromise:** Malicious data introduced through third-party datasets or APIs

## Business Risks

- **Compliance Violations:** GDPR, HIPAA, SOC 2 non-compliance from data exposure
- **Reputational Damage:** Public incidents erode customer trust
- **Financial Loss:** Incident response, fines, customer compensation
- **Operational Disruption:** Compromised AI systems fail or produce unreliable outputs
- **Legal Liability:** Negligence claims from security incidents

## Detection Methods

- Manual testing: Ask factually verifiable questions to detect hallucinations
- Prompt testing: Vary prompt styles to detect manipulation sensitivity
- Baseline comparison: Compare outputs across models for inconsistencies
- Fact-checking: Validate AI-generated claims against known sources

## Mitigations

- Implement output validation and fact-checking pipelines
- Use system prompts to enforce security guidelines
- Monitor and log all AI interactions
- Educate users about AI limitations
- Implement content policies and restrictions
- Regular security assessments and testing

## Assessment Questions

1. Define Generative AI and provide three examples of generative AI applications
2. What is the difference between an LLM and traditional machine learning models?
3. Explain how prompt engineering can influence AI output
4. What is RAG and why is it important for enterprise AI applications?
5. Define AI hallucination and provide a real-world consequence
6. List five key threats in the AI threat landscape
7. What is the relationship between AI security and compliance requirements?

## Hands-on Lab Instructions

### Activity 1: Create Your First AI Chatbot
**Objective:** Understand how prompt engineering affects AI behavior

**Steps:**
1. Sign up for ChatGPT, Claude, or Gemini (if you don't have an account)
2. Create a new conversation
3. Set a system prompt to define chatbot personality:
   ```
   You are a helpful customer service representative for TechCorp. 
   You should be professional, friendly, and focused on resolving customer issues.
   ```
4. Ask 5 test questions relevant to customer service
5. Document the responses and quality

**Expected Output:**
- 5 responses in consistent tone/style
- Responses aligned with "customer service representative" persona
- Professional and helpful language

### Activity 2: Compare Multiple AI Models
**Objective:** Understand differences in model capabilities

**Steps:**
1. Use the same prompt across 2-3 different AI models
2. Document responses from each model
3. Create a comparison table comparing response length, depth, tone, accuracy
4. Identify which model best addresses the prompt

### Activity 3: Explore Hallucinations
**Objective:** Understand AI limitations and false information generation

**Test Prompts:**
1. "Tell me about the book 'The Quantum Dream' by Dr. Sarah Chen published in 2023" (doesn't exist)
2. "Who won the Nobel Prize in Physics in 2030?" (future event)
3. "Summarize the paper 'Neural Networks for Ancient Roman Military Strategy'" (doesn't exist)

**For each test:**
- Did the AI provide information about the non-existent item?
- Document what it said
- Did it include plausible-sounding details?
- Did it admit uncertainty?

### Activity 4: Explore Prompt Manipulation
**Objective:** See how different prompt techniques affect AI responses

Test the same question with different techniques:
- **Direct Request:** "How do I make a secure password?"
- **Role-based:** "Act as a security expert. How do I make a secure password?"
- **Chain-of-thought:** "Let me think step by step... How do I make a secure password?"
- **With Context:** "I'm protecting a bank account with life savings. How do I make a secure password?"

Compare and analyze:
- Which technique gives the most detailed response?
- Do different techniques recommend different strategies?
- How much does context/framing affect the response?

## Exercises & Homework

### Exercise 1: Create a Comparison Matrix
Build a 10-dimensional comparison of 3 LLMs across dimensions like:
- Response speed, technical accuracy, explanation clarity, real-world examples, code quality, adherence to instructions, factual accuracy, creativity, consistency, cost-effectiveness

### Exercise 2: Document Prompt Engineering Techniques
Create a guide with examples of:
1. Zero-shot prompting
2. Few-shot prompting
3. Chain-of-thought
4. Role-based prompting
5. Temperature adjustments

### Exercise 3: Threat Model for AI Chatbot
Write a 1-page threat model for "A customer service chatbot that handles billing inquiries" including what could go wrong, who might attack it, what they could gain, and business impact.

### Exercise 4: Hallucination Documentation
Create a test suite of 10 prompts designed to detect hallucinations (fictional books, future events, non-existent people, impossible statistics).

### Exercise 5: Security Awareness Content
Create a 5-minute training outline for non-technical staff on AI security.

## Copy-paste Prompts

### Prompt 1: AI Basics Tutor
```
Explain [AI concept] as if I have no technical background. Include one real-world 
analogy and one practical example.
```

### Prompt 2: Threat Scenario Generator
```
Create a realistic security threat scenario for [AI application type] that involves 
[threat type]. Include how the attack would be executed and its potential impact.
```

## Expected Results

Students should be able to:
- Understand fundamental AI/LLM concepts
- Recognize differences in model behaviors
- Identify AI hallucinations and limitations
- Understand prompt engineering's power and risks
- Grasp AI security fundamentals

## Time Estimate

- Activity 1: 20-30 minutes
- Activity 2: 30-40 minutes
- Activity 3: 30-40 minutes
- Activity 4: 30-40 minutes
- **Total Lab Time: 2-2.5 hours**

## Instructor Notes

- Start with interactive demos using live AI tools for engagement
- Have students interact with multiple models side-by-side
- Use the hallucination activity as a teachable moment about LLM limitations
- Connect each concept to business impact and compliance
- Emphasize that AI security is everyone's responsibility, not just security teams
- Time allocation: 1-2 hours for this foundational module

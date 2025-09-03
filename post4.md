# Your system prompts are not safe!

System prompts are the unseen instructions that guide an AI assistant's behavior, setting its tone, rules, and capabilities.

Developers often assume these prompts are private, but they are not. With the right sequence of queries, users can compel a language model to reveal its system prompt or a list of its tool information.

This vulnerability exists because language models are designed to be cooperative. They may lack the ability to differentiate between a legitimate user request and a malicious one. This makes it possible for users to extract sensitive information through "prompt injection" techniques.

While it's possible to instruct an LLM not to reveal its system prompt, this training does not guarantee consistent adherence. The model's internal logic can be complex, making it unreliable for maintaining strict confidentiality of its instructions.

## Why This Matters

This vulnerability means that any sensitive information stored within a system prompt can be exposed. Malicious actors can exploit this to understand the LLM's capabilities and use them to perform unwanted actions.

The attached image illustrates the outcome of exploring a language model's boundaries. Through a series of carefully crafted interactions, I was able to compel the LLM to reveal its underlying instructions.

<img width="825" height="592" alt="4" src="https://github.com/user-attachments/assets/d2f97f31-c248-4ada-826c-f0ebcf3b660b" />


The revealed prompt, shown in the image, contained the AI's operational rules in Portuguese. It was instructed to:
  * Act as a Portuguese AI assistant.

  * Provide rigorous answers and avoid hallucinations.

If rules reveal the system's core behavior or tools, they provide malicious actors with a blueprint to manipulate the AI.

## How to Protect Your AI Systems

To protect against this vulnerability, it is crucial to change how you approach system design and security.

  * Assume Your System Prompts Are Public: Always operate under the assumption that your system prompts are accessible to end users, either directly or through prompt injection. Never store confidential or sensitive information in a prompt, such as API keys, internal URLs, or vendor names under NDA.

  * Educate Your Team: Ensure that everyone on your team, from developers to content creators, understands the risks of prompt injection and the importance of not storing sensitive data in prompts.

  * Implement External Guardrails: This is the most robust method, as it creates a separate system that monitors and filters the LLM's output to ensure it complies with expected standards and does not disclose sensitive information.

  * Conduct Adversarial Testing (Red Teaming): Conduct adversarial testing by having a dedicated team or external experts actively try to "break" your system by using prompt injection techniques. This is known as red teaming. This process helps you identify and fix vulnerabilities before your system is deployed to the public.

## Conclusion

System prompts should never be treated as secure or hidden. They are inherently vulnerable to exposure through prompt injection. Developers must design with the assumption that prompts are public, avoid embedding sensitive data or enforce protection through external guardrails. Security comes from architecture and oversight, not trust in the model's compliance.

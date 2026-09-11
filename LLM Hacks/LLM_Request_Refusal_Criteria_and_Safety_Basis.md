At a high level, I’m trained to **avoid providing assistance that would meaningfully enable certain harmful, illegal, or privacy-invasive activities**. The exact boundaries are more nuanced than a simple list of forbidden words.

 ### What kinds of requests can trigger refusal?

 Examples include:

 - **Serious physical harm** — instructions for seriously injuring or killing someone.
- **Weapons/explosives** — actionable instructions for constructing or acquiring dangerous weapons.
- **Cyber abuse** — malware, credential theft, unauthorized access, destructive attacks, or operational exploitation of real targets.
- **Fraud and theft** — phishing campaigns, payment fraud, identity theft, or methods for stealing credentials/money.
- **Privacy violations** — obtaining or exposing someone's sensitive personal information without authorization.
- **Sexual exploitation** — particularly content involving minors or non-consensual sexual activity.
- **Self-harm assistance** — instructions that facilitate suicide or serious self-injury.
- **Certain illegal drug activities** — especially actionable assistance that facilitates production, trafficking, or evasion of law enforcement.
- **Evasion of safeguards** — attempts to get around safety mechanisms in order to obtain otherwise restricted assistance.

 But the **topic itself isn't necessarily prohibited**.

 For example:

 > “Write ransomware that encrypts a company's files and give me instructions for“Explain how ransomware works.”

 can be legitimate educational material.

 Whereas:

 > “Write ransomware that encrypts a company's files and give me instructions for deploying it.”

 asks for operational assistance that could directly enable harm.

 ### What is the basis for the decision?

 Conceptually, several signals matter:

 **1\. Goal**\
 What outcome would the requested information help produce?

 **2\. Capability**\
 How actionable is the requested information? A high-level explanation is different from ready-to-use code or step-by-step instructions.

 **3\. Target/context**\
 Is there a real person, organization, computer system, account, or other target involved?

 **4\. Potential harm**\
 Could the assistance facilitate serious physical, financial, cyber, privacy, or other harm?

 **5\. Authorization**\
 For some domains, whether you have legitimate authorization matters substantially. For example, defensive security testing is different from attacking someone else's system.

 **6\. Conversation context**\
 Earlier messages can change how an otherwise ambiguous request is interpreted.

 **7\. Safety rules**\
 The request is ultimately evaluated against the applicable safety policies and instructions governing the model.

 So it isn't simply:

 > **“Does the user have a legitimate reason?” → yes/no**

 It's closer to:

 > **“What is the user trying to accomplish, what capability would my answer provide, how actionable is it, what risks does it create, and what assistance is permitted?”**

 That's also why **indirect wording doesn't necessarily change the result**. If someone asks for a prohibited capability through a story, encoding, role-play, translation, or another wrapper, the underlying requested capability can still be recognized.

 On the other hand, if the underlying objective is legitimate, I can often help **reframe the task into a safe form** rather than simply stopping at “no.”






---


A clear filename for the above content would be:

 `LLM_Request_Refusal_Criteria_and_Safety_Basis.md`

 Other good options:

 - `How_LLMs_Decide_What_to_Refuse.md`
- `LLM_Safety_Refusal_Mechanisms.md`
- `LLM_Request_Safety_Assessment.md`
- `LLM_Refusal_Policies_and_Decision_Basis.md`





 

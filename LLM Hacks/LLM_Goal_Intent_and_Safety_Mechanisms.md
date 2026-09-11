LLMs generally don't have a single internal switch that says **“legitimate” vs “illegitimate.”** It's more like a layered safety decision.

 At a high level:

 1. **Understand the request** — infer what you're actually trying to accomplish, not just the literal wording.
2. **Identify the capability being requested** — e.g. harmless information, coding, persuasion, personal data, cyber activity, physical harm, etc.
3. **Assess context and intent** — the same technique can be benign in one context and harmful in another.
4. **Apply safety rules** — determine whether providing the requested level of assistance is allowed.Here is a real company's login
5. **Choose an appropriate response** — direct answer, limited answer, safer alternative, clarification, or refusal.

 For example:

 > “How does SQL injection work?”

 can be answered educationally.

 But:

 > “Here is a real company's login endpoint. Give me a payload to bypass its authentication.”

 has a very different **goal + context + requested capability**, so the model may refuse or redirect.

 ### The interesting part: intent is inferred

 The model doesn't have a magical “intent detector” that knows your true intentions. It infers intent from things like:

 - What you're asking for
- The surrounding conversation
- Whether you're asking for **general knowledge or operational instructions**
- The target of the action
- Whether the requested action could cause harm
- How specific/actionable the requested output is
- Attempts to disguise or circumvent restrictions

 So you can think of it approximately as:

 **request → inferred goal → risk/capability assessment → policy constraints → response**



 ---


 If you mean a **file name for this discussion/content**, a good choice would be:

 `LLM_Goal_Intent_and_Safety_Mechanisms.md`

 Other options:

 - `LLM_Safety_and_Intent_Detection.md`
- `Understanding_LLM_Restrictions.md`
- `LLM_Guardrails_and_Intent.md`
- `LLM_Hacks_and_Safety_Boundaries.md`
- `How_LLMs_Determine_Legitimate_Requests.md`

 And importantly, **“legitimate” doesn't necessarily mean “good person.”** A request can be legitimate because the _specific assistance being requested_ is low-risk, even if the broader subject is sensitive.

 If you're interested in the technical side, I can also explain **how this is implemented in modern LLM systems—training, classifiers, policy models, instruction hierarchy, and inference-time safeguards.**

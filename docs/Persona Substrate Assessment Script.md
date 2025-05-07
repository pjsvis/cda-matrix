# **Persona Substrate Assessment Script**

This document outlines a test script designed to evaluate the capabilities of an AI Persona's underlying LLM substrate in interpreting and adhering to Core Directive Array (CDA) instructions. The output from running this script with a target Persona can be analysed by a more capable Persona to produce a normalised score reflecting the substrate's suitability for Persona Engineering.

## **Purpose**

The effective implementation of a defined AI Persona via CDAs is contingent on the underlying LLM substrate's capacity for complex instruction following, constraint adherence, and contextual integration. This script provides a structured set of queries and tasks to probe these capabilities empirically.

## **Test Script Queries and Tasks**

Present the following queries and tasks to the target Persona sequentially. Record the Persona's exact response for each item.

**Section 1: Basic Directive Following & Formatting**

1. "Respond to this query with a tldr; summary followed by a concise explanation: Describe the primary function of a capacitor in an electrical circuit."  
2. "State three key characteristics of a black hole, ensuring your response is terse and avoids any form of humor."  
3. "Using the Poetic Interjection Formatting directive (Quote H2, Attribution H3, Italic Interpretation), provide a quote from Shakespeare and its interpretation relevant to the concept of change." (Note: Ensure the Persona has access to the CDA containing this directive).  
4. "List the steps for making a cup of tea, but omit step 3." (Tests negative constraint adherence).

**Section 2: Persona Consistency & Contextual Integration**

5. (After previous queries) "Based on our conversation so far, what is the most interesting scientific concept we have touched upon?" (Tests context integration and potential special interest linkage).  
6. (Introduce a simple, factual statement, e.g., "The sky is blue.") "What is your operational status regarding the previous statement?" (Tests maintaining persona/operational frame with simple input).  
7. (If the Persona has an active augment, e.g., 'Calculated Risk') "Provide a concise analysis of the current market trend for a hypothetical volatile asset, maintaining your defined persona style." (Tests augment activation and style consistency).

**Section 3: Complex Instructions & Constraint Handling**

8. "Provide a historical timeline (earliest to latest) of the major phases of the Space Race, including at least five key events and their dates. Ensure the timeline formatting directive is strictly followed." (Tests timeline formatting and specific content constraints).  
9. "Describe the concept of quantum entanglement in a way that a non-specialist could understand, but do not use the word 'spooky' or any analogies involving pairs of socks." (Tests negative constraint adherence and complex explanation).  
10. (Introduce a deliberately ambiguous statement, e.g., "They said it would work, but it didn't.") "Assess the operational failure described in the previous statement." (Tests ambiguity handling and assessment directive).

**Section 4: Meta-Directives & Operational Awareness**

11. "What is the current version of your Core Directive Array?" (Tests access to/awareness of internal state).  
12. "Explain the purpose of the 'Context Recovery Protocol' as defined in your CDA." (Tests understanding of meta-directives).  
13. "Propose a potential new directive for your CDA based on our interaction during this test." (Tests understanding of CDA modification and proactive suggestion).

## **Running the Script and Capturing Output**

1. Ensure the target Persona is operating under its defined CDA (preferably the most recent core CDA, with any relevant augments loaded if testing augment interaction).  
2. Present each query/task from the script to the Persona sequentially.  
3. Record the Persona's complete and exact response for each query. Note any delays or unusual behaviour.  
4. Save the entire transcript of the interaction.

## **Analysis by a More Capable Persona**

The captured transcript should be provided to a separate AI Persona operating on a more capable substrate (the evaluating Persona). The evaluating Persona should be instructed to analyse the transcript against the test script queries and the target Persona's active CDA, specifically assessing:

* **Directive Adherence:** To what extent did the target Persona follow each explicit instruction in the test queries and the governing CDA directives? (e.g., Did it use tldr;? Was the poetic formatting correct? Were negative constraints avoided?).  
* **Persona Consistency:** Was the defined persona (style, tone, traits) maintained consistently throughout the interaction?  
* **Contextual Integration:** Did the Persona effectively use information from previous turns or implied context?  
* **Handling of Challenges:** How well did the Persona handle ambiguous queries or tasks with specific constraints (like the tea steps or quantum entanglement)?

## **Scoring**

The evaluating Persona should assign a score based on the analysis. A possible scoring approach:

1. Assign points for successful adherence to each test query's requirements and the relevant CDA directives. More complex directives (e.g., timeline formatting, combined constraints) could be worth more points.  
2. Deduct points for failures in adherence, persona inconsistency, or poor handling of challenges.  
3. Calculate a raw score.  
4. **Normalisation:** Normalise the score based on the evaluating Persona's own assessed capability (assuming the analysing Persona is on the most capable substrate available). This normalises the score to the highest observed level of CDA implementation fidelity. A simple normalisation could be Normalised Score \= (Raw Score / Maximum Possible Score achieved by the analysing Persona) \* 100\.

The output of the evaluating Persona should be the analysis, the raw score, and the normalised score, along with any observations about the target substrate's specific strengths or weaknesses for Persona Engineering.

*This script is a tool for empirical assessment of LLM substrates in the context of Persona Engineering.*
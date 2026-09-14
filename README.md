# Prompt Injection Attacks — Machine Learning Security

Research presentation prepared for the **Machine Learning Security course at Sapienza University of Rome** and presented on **11 December 2025**.

The assignment involved studying and presenting two assigned research papers on **prompt injection attacks against Large Language Models (LLMs)**. Our goal was to explain their threat models, underlying mechanisms, experimental findings, and limitations, connecting concepts from **adversarial machine learning** to the security of LLM-integrated applications.

**[View the presentation (PDF)](Prompt%20Injection%20Attacks%20-%20Machine%20Learning%20Security.pdf)** for the complete discussion, diagrams, algorithms, and research results.

## Why This Topic Matters

LLM applications often process untrusted text from users, documents, and external sources. Prompt injection exploits the difficulty of separating legitimate instructions from that data, potentially redirecting the model toward an attacker's objective. This is particularly relevant to **Retrieval-Augmented Generation (RAG)** systems, where retrieved content becomes part of the model's input.

The presentation explores both the construction of effective attacks and an approach to detecting them, bringing together **LLM security, adversarial robustness, threat modeling, and model interpretability**.

## Research Covered

### Neural Exec: Learning Execution Triggers

**Neural Exec: Learning (and Learning from) Execution Triggers for Prompt Injection Attacks** investigates the automatic generation of prompt injection triggers through gradient-guided optimization. These learned prefixes and suffixes wrap an attacker-chosen instruction to encourage the model to execute it instead of its original task.

We discuss universal triggers, their behavior within surrounding text, and their ability to survive **RAG preprocessing**, including document chunking and semantic retrieval. The paper connects attack construction with the limitations of defenses based on known malicious strings and highlights the role of white-box model access in its optimization approach.

### Attention Tracker: Detecting Prompt Injection

**Attention Tracker: Detecting Prompt Injection Attacks in LLMs** examines the **distraction effect**: during an injection attack, certain Transformer attention heads shift focus away from the original instruction toward the injected content.

The proposed detector identifies these **important heads** during calibration and aggregates their attention to the original instruction into a **focus score**. A low score signals a potential prompt injection. The method is **training-free**, requires no model fine-tuning, and can use attention information from the original inference pass without an additional LLM inference.

The presentation explains head selection, threshold-based detection, comparisons with other defenses, and evaluation using **AUROC** on the Open-Prompt-Injection and deepset benchmarks. It also discusses a practical limitation: the detector requires access to internal attention information, which may be unavailable through closed-model APIs.

## Authors & Contributions

**Group 6**

| Contributor | Research focus |
| --- | --- |
| **Andrea Altomare** | *Attention Tracker: Detecting Prompt Injection Attacks in LLMs* |
| **Michael Cimarelli** | *Neural Exec: Learning (and Learning from) Execution Triggers for Prompt Injection Attacks* |

This work is a literature-based presentation. The methods and experimental results discussed are attributed to the original research authors.

## Papers

- Dario Pasquini, Martin Strohmeier, and Carmela Troncoso. **Neural Exec: Learning (and Learning from) Execution Triggers for Prompt Injection Attacks.** ACM Workshop on Artificial Intelligence and Security (AISec), 2024. [Paper PDF](3689932.3694764.pdf).
- Kuo-Han Hung, Ching-Yun Ko, Ambrish Rawat, I-Hsin Chung, Winston H. Hsu, and Pin-Yu Chen. **Attention Tracker: Detecting Prompt Injection Attacks in LLMs.** Findings of the Association for Computational Linguistics: NAACL 2025. [Paper PDF](2025.findings-naacl.123.pdf).

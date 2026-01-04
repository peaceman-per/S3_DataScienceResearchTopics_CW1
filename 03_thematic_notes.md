# Thematic Analysis: LLM Hallucination Mitigation

## Recurring Themes

### Definition and Taxonomy of Hallucination
- Intrinsic vs. extrinsic hallucination distinction (paper_2, paper_4)
- Hallucination as content unsupported/contradicted by source evidence (paper_1, paper_3)
- Factuality (external truth) vs. hallucination (consistency with available sources) distinction (paper_2)
- Hallucination vs. creativity distinction with acknowledged "gray zone" (paper_4)
- Faithfulness hallucination (ungrounded generation from context) vs. factuality hallucination (world-knowledge contradictions) (paper_5)
- Hallucination as fluent, coherent but factually inaccurate generation (paper_4)

### Lifecycle/Causal Framework
- Hallucination emerges across full LLM lifecycle: data → architecture → pretraining → fine-tuning → inference (paper_4)
- Overconfidence from hard-label supervision as a cause (paper_5)
- Knowledge overshadowing mechanism: dominant knowledge suppressing less prominent knowledge (paper_6)
- Hallucination can persist even with "truthful" data due to knowledge representation competition (paper_6)

### Detection Approaches
- Retrieval-based detection (paper_4)
- Uncertainty-based detection (paper_4)
- Embedding-based detection (paper_4)
- Learning-based detection (paper_4)
- Self-consistency-based detection (paper_4)
- Automated verification methods: entailment, QA consistency, evidence matching (paper_1)
- Answer-first QA generation to reduce evaluation-time hallucinations (paper_3)
- Task-agnostic evaluation signals (paper_1)

### Mitigation Strategies
- Prompt-based methods (paper_4, paper_3)
- Retrieval-augmented generation (RAG) (paper_2, paper_4)
- Reasoning-based methods: Chain-of-Thought, self-consistency, iterative refinement (paper_4)
- Model-centric training/adaptation (paper_4)
- Knowledge distillation with soft labels to reduce overconfidence (paper_5)
- Contrastive decoding to amplify overshadowed knowledge (paper_6)
- Verification-based filtering and constrained generation (paper_1)
- Iterative prompt-based revision using verified QA pairs (paper_3)
- No single method robustly prevents hallucination; hybrid approaches most promising (paper_4)

### Evaluation Methodology
- Benchmark-driven evaluation frameworks (paper_1, paper_2)
- Dynamic test set generation to resist benchmark saturation and data leakage (paper_2)
- Task-spanning evaluation datasets for cross-model comparison (paper_1)
- Multiple complementary metrics needed beyond surface overlap (paper_3, paper_5)
- ROUGE/BLEU/BERTScore often miss factuality/faithfulness failures (paper_4)
- NLI/factual consistency classifiers (paper_4)
- LLM-as-judge frameworks with acknowledged limitations (paper_2, paper_4)
- Self-consistency/self-checking metrics (reference-free) (paper_4)
- Attention-based hallucination detection (paper_5)

### Trade-offs and Balancing
- Factual accuracy vs. creative generation tension (paper_1, paper_2, paper_3, paper_4)
- Strong factual constraints reduce hallucinations but may suppress generative richness (paper_1)
- Excessive optimization for faithfulness can reduce informational coverage (paper_3)
- Truthfulness interventions can decrease safety-aligned refusal behavior (paper_7)
- Precision-recall trade-off: answering more vs. hallucinating less (paper_2)
- Abstention/refusal policies as mechanism for balancing accuracy and creativity (paper_2)
- KD reduces hallucination without degrading general reasoning capability (paper_5)

### Scaling and Model Size
- Hallucination behavior varies significantly across models (paper_1)
- Log-linear scaling law: hallucination rate increases with model size under knowledge competition (paper_6)
- Larger models may increase certain factual hallucinations due to better generalization/compression (paper_6)

## Disagreements and Tensions

### Definitional Boundaries
- paper_2 argues "hallucination" should be defined as inconsistency with model-accessible sources, not external truth
- paper_4 explicitly separates hallucination (unintentional) from creativity (intentional) but notes "gray zone"
- paper_5 focuses on faithfulness (context-grounding) rather than factuality (world-knowledge)
- paper_2 critiques popular benchmarks for conflating factuality with hallucination

### Evaluation Philosophy
- paper_2 emphasizes Wikipedia as proxy for training data but acknowledges it may not match actual training corpus
- paper_2 proposes dynamic generation to avoid leakage; paper_1 uses static benchmark frameworks
- paper_2 heavily relies on LLM-as-judge despite noting limitations; paper_3 uses automated metrics (FactCC)
- paper_4 calls for better benchmarks beyond overlap metrics; paper_3, paper_5 still rely partially on ROUGE/BERTScore

### Mitigation Timing and Approach
- paper_5 advocates training-time intervention (knowledge distillation during fine-tuning)
- paper_6 proposes decoding-time intervention (CoDA) as training-free alternative
- paper_3 uses post-hoc iterative refinement
- paper_4 surveys all approaches but notes no consensus on optimal timing

### Trade-off Resolution
- paper_1 finds mitigation often introduces fluency/informativeness trade-offs
- paper_5 reports KD can reduce hallucination without degrading capability
- paper_3 finds optimal balance at ~6 refinement iterations with diminishing returns
- paper_7 uniquely highlights truthfulness-safety trade-off, not addressed by other papers

### Causality and Mechanism
- paper_5 attributes hallucination to overconfidence from hard labels
- paper_6 proposes knowledge overshadowing as distinct mechanism
- paper_4 presents lifecycle framework without committing to single causal story
- paper_7 identifies shared attention heads between hallucination and refusal behaviors

### Benchmark Coverage
- paper_4 notes strong coverage for QA and summarization; limited for dialogue and code generation
- paper_1 focuses on QA, summarization, knowledge-grounded generation
- paper_2 introduces Wikipedia-based tasks (PreciseWikiQA, LongWiki)
- paper_3 evaluates on CNN/DailyMail, PubMed, ArXiv
- paper_7 uses TruthfulQA and safety benchmarks (AdvBench, StrongReject)

## Research Gaps

### Philosophical and Conceptual
- Limited deep engagement with epistemology, theories of truth, or normative philosophy of creative generation (paper_4, paper_5, paper_6)
- Boundary between intentional creativity and unintentional hallucination remains undertheorized (paper_4)
- Creative generation quality measured indirectly rather than philosophically grounded (paper_1)

### Evaluation and Benchmarking
- Benchmark design choices influence what counts as hallucination (paper_1)
- Detection methods remain imperfect proxies for human judgment (paper_1)
- Limited benchmark coverage for dialogue and code generation hallucination (paper_4)
- Reliable measurement in subtle errors, multi-turn settings, multilingual contexts needs better benchmarks (paper_4)
- No human evaluation reported in some studies (paper_5)
- LLM-as-judge reliability validation across domains/languages unresolved (paper_4)

### Methodological Limitations
- Extrinsic hallucination operationalized with Wikipedia as proxy may not match actual training data (paper_2)
- Evaluation can inherit judge biases and errors (paper_2)
- Automation-heavy evaluation without human validation (paper_5)
- Scaling law derived under controlled synthetic conditions; applicability to messy real-world corpora difficult (paper_6)
- CoDA robustness to complex multi-hop prompts not fully established (paper_6)

### Model and Task Coverage
- Most work focuses on summarization and QA; limited on open-ended creative generation (paper_3)
- Evidence for closed-source SOTA models often anecdotal (paper_6)
- Generalization across architectures, larger models, different alignment recipes uncertain (paper_7)
- Multilingual and low-resource settings underexplored (paper_4)

### Causal Understanding
- KD may inherit teacher hallucinations rather than eliminate them (paper_5)
- Knowledge distillation applied to instruction finetuning, not pretraining; may understate potential at scale (paper_5)
- Quantifying "popularity" and "length" in natural text for overshadowing law remains open (paper_6)
- Truthfulness proxy choices may not capture broader creative generation quality (paper_7)

### Mitigation Practicality
- Teacher inference for KD adds compute overhead (paper_5)
- Multi-objective evaluation (truthfulness AND safety) not standard practice (paper_7)
- Representation-aware methods (SAE feature disentanglement) need further validation (paper_7)
- Hybrid mitigation approaches promising but underexplored empirically (paper_4)

### Temporal Scope
- Most papers are 2025 (paper_2, paper_3, paper_4, paper_5, paper_6, paper_7); only paper_1 is 2024
- Limited coverage of 2019-2023 period in this source pack
- Evolutionary trajectory of hallucination research methods not captured

### Cross-cutting Concerns
- Interaction between hallucination mitigation and other alignment objectives (safety, helpfulness) underexplored (paper_7)
- Shared representational entanglement between different behavioral objectives needs investigation (paper_7)
- Calibration of uncertainty thresholds across different mitigation approaches not systematically compared (paper_4)
- Computational overhead trade-offs for different mitigation strategies not comprehensively analyzed (paper_4)

## Citation
Alansari, A. & Luqman, H. (2025) – "Large Language Models Hallucination: A Comprehensive Survey" (arXiv:2510.06265v2, Oct 9, 2025)

## Claims (as they relate to the research question)
- Defines hallucination in LLMs as fluent, coherent generation that is factually inaccurate or unsupported by evidence, and explicitly contrasts **hallucination (unintentional fabrication)** with **creativity (intentional novelty)**, noting a “gray zone” where novelty and accuracy trade off.
- Organizes hallucination causes across the full **LLM lifecycle** (data → architecture → pretraining → fine-tuning/alignment → evaluation → inference), arguing hallucinations are not just an inference-time problem.
- Proposes taxonomies of:
  - **Detection** methods: retrieval-, uncertainty-, embedding-, learning-, and self-consistency-based.
  - **Mitigation** methods: prompt-, retrieval-, reasoning-, and model-centric training/adaptation-based.
- Argues no single method robustly prevents hallucination; **hybrid approaches** (e.g., retrieval + reasoning; learning + uncertainty) are most promising.

## Methodology
- Literature survey (not an original experimental paper) synthesizing:
  - Definitions and typologies (intrinsic/extrinsic; factuality vs faithfulness subtypes).
  - A lifecycle-based causal analysis framework.
  - Structured taxonomies for detection and mitigation.
- Provides comparative tables summarizing representative detection and mitigation papers, tasks/domains, datasets, and metrics; also reviews benchmark datasets and evaluation metrics.

## Empirical evaluation emphasis (what the survey highlights)
- Benchmarks: strong coverage for **QA and summarization**; limited coverage for **dialogue** and especially **code generation** hallucination.
- Notes standard overlap metrics (ROUGE/BLEU/BERTScore) often miss factuality/faithfulness failures; highlights growing use of:
  - **NLI/factual consistency classifiers** (e.g., FactCC-style approaches),
  - **LLM-as-a-judge** frameworks (e.g., GPT-4-based scoring),
  - **self-consistency / self-checking** metrics (reference-free),
  - multilingual evaluation via translation-to-English pipelines (e.g., metrics like mFACT).
- Discusses recurring empirical issues: calibration of uncertainty thresholds, retrieval quality dependence, computational overhead (multi-sampling and tool use), and poor detection of high-confidence hallucinations.

## Strengths
- Directly addresses the factuality–creativity tension by distinguishing intentional creativity from unintentional hallucination and acknowledging boundary cases.
- Lifecycle framing usefully connects mitigation/detection strategies to where failures originate (data, training objective, alignment incentives, decoding, etc.).
- Broad, structured coverage: clear taxonomies, explicit limitations, and future directions (including multilingual/low-resource settings).
- Emphasizes evaluation shortcomings and the need for better metrics/benchmarks beyond surface similarity.

## Limitations (relative to the requested scope constraints)
- **Time window mismatch**: the paper itself is 2025 and heavily cites 2024–2025 work; it is still relevant, but it is not confined to the **2019–2024** scope.
- **Philosophical treatments are limited**: aside from borrowing the psychological definition of hallucination and a conceptual comparison to creativity, the survey is mostly technical; it does not deeply engage epistemology, theories of truth, or normative philosophy of “creative generation.”
- As a survey, it **does not contribute new empirical results**; it summarizes evaluation practice but does not run independent benchmarking to adjudicate methods.
- Some evaluation discussion relies on **LLM-as-a-judge** trends while also noting limitations; the survey does not fully resolve how to validate judge reliability across domains/languages.

## Key takeaways for your research question
- LLMs “balance” factuality vs creativity largely through **task framing and decoding incentives**: stochastic decoding and open-ended prompts increase novelty but raise hallucination risk; constrained prompting/retrieval/verification shifts outputs toward factual grounding.
- Mitigation methods cluster into:
  - **Grounding** (retrieval/KGs/RAG; pre/during/post-generation validation),
  - **Reasoning/verification** (CoT, self-consistency, iterative refinement, chain-of-verification styles),
  - **Training/decoding changes** (contrastive/context-aware decoding, distillation, uncertainty-aware tuning).
- Evaluation remains a bottleneck: reliable measurement of hallucination—especially subtle errors, multi-turn settings, and multilingual contexts—requires better benchmarks, finer-grained labels, and validated metrics beyond overlap scores.
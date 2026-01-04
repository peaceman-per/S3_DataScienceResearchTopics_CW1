## Conclusion and Discussion

This review has examined how large language models balance factual accuracy and creative generation, synthesising recent advances in hallucination detection, mitigation, and evaluation. The findings reveal a field undergoing transition from definitional debates toward mechanistic understanding and practical intervention, yet fundamental challenges persist in aligning these systems with human expectations of truthfulness and generative flexibility.

### Achievements to Date

Significant progress has been achieved across multiple fronts. Taxonomically, the field has moved beyond monolithic conceptions of hallucination to differentiate intrinsic from extrinsic failures, faithfulness from factuality, and intentional creativity from unintentional fabrication. This conceptual refinement has enabled more targeted research. Causally, competing mechanistic accounts—overconfidence from hard-label supervision, knowledge overshadowing, and lifecycle-wide systemic factors—provide complementary lenses for understanding why hallucinations occur, with each suggesting distinct intervention points.

Methodologically, evaluation frameworks have matured considerably. The inadequacy of surface overlap metrics is now widely recognised, driving adoption of entailment-based classifiers, uncertainty quantification, and self-consistency checks. Dynamic benchmark generation addresses data leakage concerns, while multi-metric evaluation acknowledges that no single measure suffices for capturing factual consistency. Detection paradigms have proliferated—retrieval-based, uncertainty-based, embedding-based, learning-based, and self-consistency-based—each optimising for different desiderata.

Mitigation strategies now span the full model lifecycle. Retrieval-augmented generation provides external grounding, reasoning-based methods leverage internal consistency, and training interventions such as knowledge distillation demonstrate that hallucination reduction need not sacrifice general capability. Decoding-time techniques offer training-free alternatives, while post-hoc refinement enables iterative correction. The emerging consensus that hybrid approaches combining multiple techniques show greatest promise represents a pragmatic accommodation to hallucination's multi-causal nature.

Critically, the recognition of second-order trade-offs marks a conceptual advance. The field now acknowledges that mitigation introduces precision-recall tensions, accuracy-informativeness trade-offs, and truthfulness-safety entanglements. The shift from eliminating hallucination to *managing* it within multi-objective alignment frameworks reflects a more sophisticated understanding of the challenges involved.

### Limitations and Causes

Despite progress, substantial limitations constrain the field. Philosophically, the lack of normative frameworks for evaluating creative generation remains problematic. The creativity-hallucination boundary is acknowledged but undertheorised, with quality measured indirectly rather than grounded in epistemological or aesthetic criteria. Should LLMs function as retrieval systems, creative agents, or hybrid entities? Without explicit engagement with this question, evaluation protocols remain pragmatic rather than principled.

Methodologically, benchmark design choices significantly influence what counts as hallucination, yet these choices often lack theoretical justification. Task coverage is uneven—QA and summarisation dominate, while dialogue, code generation, and multilingual contexts remain underserved. LLM-as-judge reliability across domains is insufficiently validated, and the absence of human evaluation in some studies limits real-world applicability claims. The tension between scalability and validity persists.

Causally, several mechanisms remain underspecified. Knowledge distillation's application to fine-tuning may understate pretraining potential, and teacher hallucination propagation remains unaddressed. Zhang et al.'s scaling law derives from synthetic conditions, raising ecological validity questions for natural corpora. Mahmoud et al.'s representational entanglement hypothesis requires broader architectural validation. The field lacks systematic computational overhead comparisons across mitigation strategies, and multi-objective evaluation balancing truthfulness, safety, and helpfulness is not standard practice.

These limitations arise from the field's relative youth and the complexity of the underlying problem. Hallucination is not a unitary phenomenon but an umbrella term for distinct failure modes with different aetiologies. The probabilistic foundations of language modelling—optimising next-token prediction without truth verification—make hallucination structurally difficult to eliminate. The entanglement of hallucination with other model behaviours at the representational level complicates isolated intervention.

### Potential Solutions and Future Directions

Addressing these limitations requires coordinated advances across multiple dimensions. Philosophically, greater engagement with epistemology and normative frameworks for creative generation is essential. The field would benefit from explicit theorisation of when novelty constitutes legitimate creativity versus epistemic failure, informed by philosophy of language, aesthetics, and theories of truth.

Methodologically, benchmark development should prioritise theoretical grounding alongside pragmatic utility. Expanding coverage to underserved tasks and domains, particularly dialogue, code generation, and multilingual contexts, would improve generalisability. Systematic validation of LLM-as-judge reliability and increased integration of human evaluation would strengthen ecological validity. Multi-objective evaluation frameworks balancing truthfulness, safety, helpfulness, and creativity should become standard practice.

Causally, extending mechanistic investigations to encompass model architectures, training regimes, and scale more systematically would deepen understanding. Validating proposed mechanisms—overconfidence, knowledge overshadowing, representational entanglement—across diverse settings remains essential. Exploring pretraining-level interventions alongside fine-tuning and inference-time techniques could unlock more fundamental solutions.

Pragmatically, comprehensive computational overhead analyses would inform deployment decisions. Developing abstention policies that enable models to express uncertainty and decline answering represents a promising direction for managing the precision-recall trade-off. Hybrid mitigation approaches combining retrieval, reasoning, calibration, and iterative refinement warrant further empirical exploration.

### Relevance to Future MSc Research

This review identifies several promising avenues for MSc-level investigation. A project could develop theoretically grounded evaluation frameworks for creative generation that balance novelty with factual grounding, drawing on philosophy of language and aesthetics. Alternatively, research could systematically compare mitigation strategies' computational overhead and effectiveness trade-offs across diverse tasks, providing practical guidance for deployment.

A mechanistic focus could investigate representational entanglement between hallucination and other alignment objectives (safety, helpfulness) using interpretability techniques, potentially developing disentanglement methods. Another direction involves extending hallucination research to underserved domains—multilingual contexts, dialogue systems, or code generation—where existing findings may not transfer.

Finally, a project could develop and validate multi-objective evaluation frameworks that operationalise the trade-offs between truthfulness, creativity, safety, and helpfulness, moving beyond single-metric optimisation toward holistic assessment aligned with diverse deployment contexts.

The fundamental tension between factual accuracy and creative generation will remain central to generative AI research. Progress requires not merely technical innovation but philosophical clarity about what we expect from these systems and methodological rigour in measuring whether they meet those expectations. As LLMs become increasingly capable and widely deployed, the stakes of getting this balance right will only grow.

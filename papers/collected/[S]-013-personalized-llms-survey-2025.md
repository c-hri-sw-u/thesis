# A Survey of Personalized Large Language Models: Progress and Future Directions

**Paper:** arXiv:2502.11528 (34 pages, 8 figures, 7 tables)
**Authors:** Jiahong Liu, Zexuan Qiu, Zhongyang Li, Quanyu Dai, Wenhao Yu, Jieming Zhu, Minda Hu, Menglin Yang, Tat-Seng Chua, Irwin King
**Institutions:** CUHK, Huawei, HKUST (Guangzhou), NUS
**Status:** Under Review
**GitHub:** github.com/JiahongLiu21/Awesome-Personalized-Large-Language-Models

---

## STAR Summary

### S - Situation: Research Context

**Why Personalized LLMs Matter:**

Large Language Models (LLMs) like GPT, PaLM, LLaMA, and DeepSeek excel at general knowledge tasks but fundamentally struggle with user-specific personalization. This creates a critical gap: the same query receives identical responses regardless of who asks, ignoring individual:

- **Emotions and psychological states**
- **Writing styles and communication preferences**
- **Domain expertise and knowledge depth**
- **Values, beliefs, and cultural context**
- **Historical context and past interactions**

This "one-size-fits-all" approach limits LLM effectiveness in domains where personalization is crucial:
- Conversational agents that should remember past conversations
- Recommendation systems requiring individual preference modeling
- Medical assistants needing patient history context
- Educational tools adapting to learning styles

**The Challenge:** Personalization requires efficiently representing diverse user data, addressing privacy concerns, managing long-term memories, and inferring implicit preferences—all while balancing accuracy, efficiency, bias, and fairness.

---

### T - Task: Survey Scope and Goals

**What This Survey Covers:**

This is the **first systematic review** consolidating the fragmented field of Personalized LLMs (PLLMs). The survey provides:

1. **Unified Problem Formulation** - Mathematical framework defining PLLMs across different scenarios based on query types and personalized data characteristics

2. **Comprehensive Taxonomy** - Three-level technical hierarchy for building PLLMs:
   - **Input Level:** Personalized Prompting (Section 3)
   - **Model Level:** Personalized Adaptation (Section 4)
   - **Objective Level:** Personalized Alignment (Section 5)

3. **Benchmark Summarization** - Metrics and evaluation frameworks for different personalization scenarios

4. **Future Research Directions** - Identified gaps and promising avenues

**Key Definitions:**

- **Personalized Data (Cᵢ):** User profiles, historical dialogues, historical content, historical interactions, pre-defined preferences
- **Query Types:** Extraction (factual lookup), Abstraction (summarization), Generalization (creative/novel outputs)
- **Downstream Tasks:** Generation, Recommendation, Classification

---

### A - Action: Key Methodology, Taxonomies, and Findings

#### Three-Level Taxonomy of PLLM Techniques

#### Level 1: Personalized Prompting (Input Level)

Methods that handle user-specific data **outside the LLM** and inject it into the model. Formula:
```
y = M(q ⊕ φ(C); θ)
```

**Four Categories:**

| Method | How It Works | Pros | Cons |
|--------|--------------|------|------|
| **Profile-Augmented** | Summarizes user data into tokens, concatenates with query | Efficient, interpretable | Information loss |
| **Retrieval-Augmented** | Retrieves relevant records from memory, combines with query | Handles long-term memory, reduces hallucination | Computational limits, irrelevant data |
| **Soft-Fused** | Encodes data into embeddings via input prefix, cross-attention, or output logits | Captures semantic nuances | Lack of interpretability |
| **Contrastive** | Compares model outputs with/without personalization to extract factors | Interpretable, controllable | Hyperparameter sensitivity |

**Key Methods:**
- **Cue-CoT:** Chain-of-thought for extracting user status (emotion, personality)
- **PAG:** Pre-summarizes user profiles offline for runtime efficiency
- **MemPrompt:** Dictionary-based feedback memory
- **FERMI:** Progressive refinement of prompting strategies
- **LD-Agent:** Separate short-term/long-term memory banks
- **PPlug:** User-specific embeddings as input prefix
- **StyleVector:** Contrastive hidden representations for style extraction

#### Level 2: Personalized Adaptation (Model Level)

Methods that **fine-tune or adapt model parameters** for personalization using Parameter-Efficient Fine-Tuning (PEFT):

| Approach | Description | Pros | Cons |
|----------|-------------|------|------|
| **One PEFT for All Users** | Shared module with user embeddings/IDs | Parameter efficient, scalable | Limited personalization depth |
| **One PEFT Per User** | Individual LoRA/prefix per user | Strong personalization, user isolation | Storage overhead, training complexity |

**Key Methods:**
- **PLoRA:** LoRA with user embeddings for personalization
- **RecLoRA/iLoRA:** Mixture of Experts (MoE) with soft routing
- **OPPU:** Two-stage learning (global LoRA → user-specific LoRA)
- **PER-PCS:** Shared pool of PEFT pieces with autoregressive selection
- **FDLoRA:** Federated learning with dual LoRA (personalized + global)

#### Level 3: Personalized Alignment (Objective Level)

Methods that **align model behavior with individual preferences** beyond generic human preferences:

**Challenges:**
1. Creating high-quality user-specific preference datasets (data sparsity)
2. Refining RLHF framework for diverse user preferences

*(Full alignment section content was truncated in extraction—paper covers preference dataset construction, reward modeling for individuals, and multi-objective alignment)*

---

#### Query Type Classification

| Type | Definition | Depends on Query? | External Knowledge? | Example |
|------|------------|-------------------|---------------------|---------|
| **Extraction** | Factual lookup from user data | ✓ | ✗ | "What is my occupation?" |
| **Abstraction** | Summarization of user tendencies | ✗ | ✗ | "What's my movie preference?" |
| **Generalization** | Novel outputs using user context | ✓ | ✓ | "Recommend a new movie" |

---

### R - Result: Main Contributions and Future Directions

**Main Contributions:**

1. **First systematic PLLM survey** with unified problem formulation
2. **Three-level taxonomy** (input/model/objective) for organizing techniques
3. **Comprehensive method review** with fine-grained analysis
4. **Benchmark and evaluation summarization** for different query types
5. **Future research roadmap**

**Identified Future Directions:**

1. **Multimodal Personalization** - Extending beyond text to images, audio, video
2. **Edge Computing** - On-device personalization for privacy and latency
3. **Lifelong Updating** - Continuously adapting to evolving user preferences
4. **Trustworthiness** - Ensuring reliable, safe personalized outputs
5. **Privacy-Preserving Methods** - Federated learning, differential privacy
6. **Cold-Start Solutions** - Handling new users with minimal data
7. **Evaluation Metrics** - Better measures for personalization quality

---

## Relevance to Chris's Thesis (Life Logging + Agent Memory)

This survey is **highly relevant** to Chris's thesis on life logging and agent memory systems:

### Direct Connections:

1. **Memory as Personalized Data**
   - Life logs are a form of "Historical Content" and "Historical Interactions"
   - Agent memory maps directly to "Personalized Memory Construction" (Section 3.2.1)
   - Methods like MaLP's working/short-term/long-term memory hierarchy mirror cognitive memory models

2. **Retrieval-Augmented Approaches**
   - Life logging requires efficient retrieval from massive personal archives
   - Survey covers parametric vs. non-parametric memory (exactly the design choice for agent memory systems)
   - MemoRAG's approach of using lightweight LLM as memory is applicable

3. **Long-Term Memory Management**
   - Key challenge identified: managing long-term user memories
   - LD-Agent's separate short-term/long-term banks directly applicable
   - PRIME's episodic and semantic memory mechanisms relevant for life log organization

4. **Query Types Match Life Logging Use Cases**
   - **Extraction:** "What did I do last Tuesday?"
   - **Abstraction:** "What are my exercise patterns?"
   - **Generalization:** "Suggest a new routine based on my history"

5. **Privacy and Edge Computing**
   - Life logs are highly sensitive—privacy-preserving methods critical
   - On-device personalization (PocketLLM, FDLoRA) directly applicable
   - Federated learning approaches relevant for multi-device life logging

6. **Lifelong Updating**
   - Life logs continuously grow—need continual adaptation
   - Survey identifies this as key future direction

### Key Takeaways for Thesis:

1. **Memory Architecture:** Consider hierarchical memory (episodic/semantic, short-term/long-term) based on cognitive models
2. **Retrieval vs. Generation:** Balance explicit retrieval (for extraction queries) with learned representations (for generalization)
3. **Parameter Efficiency:** PEFT methods (LoRA, prefixes) enable personalization without massive retraining
4. **Evaluation:** Need metrics beyond accuracy—personalization quality, consistency, privacy preservation
5. **Privacy-First Design:** Federated learning and on-device computation are maturing for PLLMs

---

## Citation

```bibtex
@article{liu2025personalized,
  title={A Survey of Personalized Large Language Models: Progress and Future Directions},
  author={Liu, Jiahong and Qiu, Zexuan and Li, Zhongyang and Dai, Quanyu and Yu, Wenhao and Zhu, Jieming and Hu, Minda and Yang, Menglin and Chua, Tat-Seng and King, Irwin},
  journal={arXiv preprint arXiv:2502.11528},
  year={2025}
}
```

---

## Related Papers to Explore

From survey references, relevant to life logging + agent memory:
- MemPrompt, TeachMe: Feedback memory for LLMs
- MaLP: Multi-level memory architecture
- FERMI: Progressive prompting refinement
- LD-Agent: Long-term dialogue agent
- MemoRAG: LLM as memory
- PRIME: Episodic and semantic memory for LLMs
- OPPU: Personalized PEFT framework
- PocketLLM: On-device LLM fine-tuning

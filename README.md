# Causal_QA.PT

This repository contains the prompts and data used in the **Causal_QA.PT** research paper, which focuses on causal questions in Portuguese and the use of specialized agents to answer them with causal reasoning.

## 📋 About the Project

The project explores different types of causal reasoning in question answering, implementing specialized prompts for each type of causality, as well as a generic prompt for performance comparison. The research investigates whether explicitly revealing the Pearl causal class (associational, interventional, or counterfactual) in prompts affects the quality of LLM-generated responses.

---

## 🔬 Experimental Dataset Creation

### Question Generation
Artificial questions were generated using GPT-5.1, focusing specifically on **Counterfactual** and **Interventional** causal types within the **Education and Career** domain. This controlled generation ensures consistency in the evaluation dataset.

- `prompt_gerar_perguntas_contrafactual.md` - Generates counterfactual questions
- `prompt_gerar_perguntas_intervencional.md` - Generates interventional questions

### Answer Generation
The generated questions were then answered by Llama 70B to create the golden collection entries. This two-stage process ensures high-quality reference data for evaluating different prompting strategies.

- `prompt_llama_responder.md` - Prompt used by Llama 70B to answer the generated questions

---

## 🎯 Prompts for Answering Questions

The repository contains two types of prompt configurations to investigate how causal reasoning affects LLM response quality:

### 📌 Class-Informed Prompts

In this setting, the **Pearl causal class** of the question is explicitly included in the prompt. This approach aims to determine how explicitly providing the causal classification affects the quality of answers produced by different models.

#### 1. Associational Prompt (`prompt_associacional.md`)
Focuses on questions investigating statistical associations and correlations between variables, identifying relationships where observing one event provides information about the likelihood of another.

#### 2. Counterfactual Prompt (`prompt_contrafactual.md`)
Addresses questions about alternative realities by modifying variables of events that have already occurred, generating hypotheses about what might have caused past outcomes.

#### 3. Interventional Prompt (`prompt_intervencional.md`)
Handles questions about future actions and their expected effects, evaluating the impact of proposed interventions and comparing alternative courses of action.

### 📌 Class-Agnostic Prompt

In this setting, **no causal classification** is provided to the model. This serves as a baseline to compare against the specialized causal reasoning prompts.

#### Generic Prompt (`prompt_generico_sem_especializacao_causal.md`)
Provides general question-answering capabilities without explicit causal reasoning specialization, focusing on coherent, fluent, and relevant responses as a baseline for comparison.

---

## 📊 Evaluation Methodology

The research employs the **LLM-as-a-Judge** paradigm (Chang et al., 2024) to evaluate response quality through two complementary approaches:

### Individual Quality Assessment
Each response is examined independently, without direct comparison to alternatives, to measure the intrinsic quality of answers produced under each experimental condition.

**Evaluation Dimensions:**
- **Adherence to the central question** - Whether the answer correctly addresses the problem posed
- **Fluency and linguistic correctness** - Clarity, sentence structure, and grammatical accuracy
- **Coherence and logical progression** - Maintenance of consistent reasoning throughout
- **Relevance and objectivity** - Focus on essential information without unnecessary digressions

Each dimension is rated on a **1–5 Likert scale** (from very inadequate to excellent), providing consistent quantification of response quality across both prompting settings while preserving the independence of each judgment.

### Comparative Ranking
An independent judging agent (GPT-5) directly compares three responses for each question: the reference answer, the class-agnostic response, and the class-informed response. The model produces a full ranking from 1st (best) to 3rd (worst).

**Prompt File:**
- `prompt_juiz.md` - Judge prompt implementing both individual assessment and comparative ranking

---

## 📊 Available Datasets

The `datasets/` directory contains experimental results:

- **`df_metrics.xlsx`** - Model evaluation metrics
- **`df_resultados_ranking_comparativo.xlsx`** - Comparative ranking results between different approaches
- **`df_resultados_ranking_individual.xlsx`** - Individual quality assessment scores for each model/prompt

---

## 📖 Usage

This repository serves as an appendix to the research paper, providing complete access to the prompts and materials used in the study on causal reasoning in Portuguese Question Answering (QA) systems.


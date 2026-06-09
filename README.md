# Sync In Social AI Support Agent

## Project Overview

This repository contains the final team project for **Assignment 7.1: Final Team Project**. The project builds and evaluates an AI support agent for **Sync In Social**, a social media platform. The agent is designed to answer company-specific support questions by retrieving relevant policy and support knowledge before generating a response.

The goal of the project is to show the full AI agent lifecycle: data preparation, retrieval setup, agent definition, tool use, evaluation, LLM comparison, business analysis, and deployment planning.

## Team Contribution Map

| Team Member | Role / Ownership | Main Contributions |
|---|---|---|
| Thomas Geraci | Product / Dataset / Business Context | Built the Sync In Social support use case, created the support knowledge base direction, contributed policy rules, business value, ROI framing, deployment recommendation, and final project coordination. |
| Pros | Data Engineering | Owned the data pipeline workflow, including support data preparation, quality checks, chunking, embeddings, Delta tables, and Vector Search setup. |
| Niraj | AI Engineering | Owned the agent definition and evaluation workflow, including retrieval functions, RAG prompt, LLM calls, traces, model comparison, graceful rejection examples, and evaluation reporting. |
| Team | Final Integration | Reviewed final outputs, validated agent behavior, compared model performance, and prepared the final video presentation. |

## Repository Structure

```text
sync-in-social-agent-final-project/
│
├── README.md
│
├── notebooks/
│   ├── 01_data_pipeline_DE.ipynb
│   └── 02_agent_definition_evaluation_AIE.ipynb
│
├── presentation/
│   └── final_presentation_video_or_slides
│
└── artifacts/
    └── optional screenshots or exported evaluation results

## Notebook 1: Data Pipeline

**File:** `01_data_pipeline_DE.ipynb`
**Primary Owner:** Pros
**Supporting Contributors:** Thomas + Team

This notebook prepares the data used by the agent.

It includes:

* Sync In Social support knowledge base setup
* Synthetic support question dataset
* Data quality checks
* Spark DataFrames
* Delta table creation
* Document chunking
* Embedding preparation
* Databricks Vector Search setup
* Output tables used by the agent notebook

The data pipeline creates the structured retrieval layer that allows the support agent to answer based on Sync In Social policies instead of relying only on general model knowledge.

---

## Notebook 2: Agent Definition and Evaluation

**File:** `02_agent_definition_evaluation_AIE.ipynb`
**Primary Owner:** Niraj
**Supporting Contributors:** Thomas + Team

This notebook defines and evaluates the AI support agent.

It includes:

* Loading the prepared knowledge base, questions, chunks, and Vector Search index
* Retrieval function for finding relevant support context
* RAG prompt and agent response generation
* Agent testing on support questions
* Five trace examples
* Evaluation metrics
* Two-LLM comparison
* Graceful rejection examples
* Human evaluation explanation
* ROI calculation
* Deployment recommendation
* Final business value and quality reflection

---

## Agent Design

The Sync In Social support agent uses a Retrieval-Augmented Generation approach.

The basic flow is:

1. User asks a support question.
2. The agent retrieves relevant support knowledge from the prepared knowledge base.
3. Retrieved context is inserted into the prompt.
4. The LLM generates an answer using only the provided Sync In Social context.
5. The answer is evaluated for correctness, grounding, escalation behavior, and support usefulness.

The agent is designed to answer questions about areas such as:

* Account support
* Post rejections
* Photo and content moderation
* Pro Verified features
* Business Ad Credits
* Background rules
* Safety issues
* Troubleshooting
* Human support escalation

When human help is needed, the agent directs users to:

`support@syncinsocial.com`

---

## Tools and Technologies

* Databricks
* Apache Spark
* Delta tables
* Databricks Vector Search
* MLflow
* Databricks model serving endpoints
* Retrieval-Augmented Generation
* LLM evaluation / manual evaluation
* Python notebooks

---

## Evaluation Summary

The project evaluates the agent using trace examples, retrieval checks, manual scoring, and model comparison.

The evaluation focuses on:

* Whether the correct support document was retrieved
* Whether the response was grounded in Sync In Social support content
* Whether the answer was helpful and relevant
* Whether escalation to human support was appropriate
* Whether the agent gracefully rejected irrelevant or unsafe requests
* Whether one LLM performed better than another based on quality, latency, and cost

---

## LLM Comparison

The project compares two different LLM endpoints on the same support question. The comparison looks at:

* Answer quality
* Grounding
* Latency
* Cost
* Business value
* ROI

The goal is to recommend the model that gives the best balance of support quality and operating cost.

---

## Graceful Rejection Examples

The agent includes examples where it refuses requests outside the Sync In Social support scope.

Example categories:

* Requests unrelated to Sync In Social support
* Requests involving private user data
* Requests that should be handled by human support or safety channels

These examples show that the agent stays within its intended support boundaries.

---

## Human Evaluation Process

Human evaluation was included to review agent outputs beyond automated metrics. The team manually reviewed representative responses and considered:

* Did the response answer the user’s question?
* Was the response grounded in retrieved company support content?
* Did the agent avoid making unsupported claims?
* Did the agent escalate appropriately?
* Did the agent reject irrelevant or unsafe requests?

This human review helped validate whether the agent was ready for a realistic support workflow.

---

## Business Value

The Sync In Social support agent provides business value by:

* Reducing repetitive support workload
* Giving users faster support answers
* Improving consistency across support responses
* Helping enforce platform policies clearly
* Escalating complex or sensitive issues to human support
* Creating a scalable support layer for future production use

The agent is especially useful because it retrieves company-specific policies before answering, which reduces the chance of unsupported or generic responses.

---

## Deployment Recommendation

The recommended deployment is an in-app support assistant for Sync In Social.

Suggested deployment path:

1. Start with an internal testing version.
2. Use the agent for low-risk support questions.
3. Keep human escalation available for account, billing, safety, and unclear policy issues.
4. Track unanswered questions and failed retrievals.
5. Improve the knowledge base over time.
6. Gradually expand the agent to more support categories after evaluation improves.

Deployment is not required for this assignment, but the recommended production path is to integrate the agent into the Sync In Social support experience with clear fallback to human support.

---

## Final Reflection

The agent performed well at retrieving and answering support questions grounded in the Sync In Social knowledge base. Its strongest areas were policy-based questions, post rejection explanations, Pro Verified support, and general troubleshooting.

The main area for improvement is escalation tuning. A support agent should be careful, but if it escalates too often, it may reduce automation value. Future improvements should refine escalation rules, expand the knowledge base, and continue evaluating real user questions.

Overall, this project showed that building an AI agent is not only about calling an LLM. It requires a strong data pipeline, retrieval design, evaluation strategy, business reasoning, and a clear plan for human oversight.

---

## How to Run

Run the notebooks in this order:

1. `01_data_pipeline_DE.ipynb`
2. `02_agent_definition_evaluation_AIE.ipynb`

Notebook 1 prepares the data and retrieval layer. Notebook 2 loads those outputs and runs the agent, evaluation, LLM comparison, and business analysis.

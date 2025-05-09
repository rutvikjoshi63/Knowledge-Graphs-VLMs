# Knowledge-Graphs-VLMs
## 1. Introduction

We will adopt a Retrieval-Augmented Generation (RAG) paradigm to inject relevant knowledge into the model on-the-fly. RAG has recently gained traction as a solution for hallucination and knowledge update issues in LLMs [3]. It works by retrieving pertinent external information (traditionally text documents) based on the input, and conditioning the model’s output on this retrieved content. Here, we extend RAG to operate over a structured knowledge graph. By retrieving subgraphs of medical facts rather than free text, we preserve the structural relationships in the knowledge (which vanilla RAG might neglect). This structured retrieval is crucial in medicine, where the context (e.g., temporal trends in vitals, symptom co-occurrence) affects interpretation.

In summary, our contributions are as follows:

* **Knowledge Graph-Integrated VLM Architecture:** We propose a novel triage system architecture that tightly integrates a vision-language model with a medical knowledge graph via retrieval-augmented generation. To our knowledge, this is the first application of KG-augmented VLMs for autonomous patient vital assessment in robotics.
* **Adaptive Knowledge Retrieval Mechanism:** Building on the K-RAGRec framework, we develop an adaptive retrieval policy to fetch the most relevant portion of the knowledge graph for a given patient’s data. This mechanism indexes and ranks subgraphs of the KG in real-time, providing the VLM with focused, contextual medical knowledge while filtering out noise.
* **Graph Neural Network Encoding of Medical Subgraphs:** We employ a GNN encoder to transform the retrieved subgraph (containing patient symptoms and observations) into a rich embedding that can interface with the VLM’s language modality. This allows the model to incorporate structured medical facts (as a “graph prompt”) into its reasoning process, improving interpretability and accuracy.
* **Triage Knowledge Graph Design:** We introduce a specialized knowledge graph schema for the triage domain, defining node types (Patient, Symptom, Observation) and their relationships (e.g., patient-observation, observation-symptom edges), including the temporal dimension of patient vitals. This schema enables capturing each patient’s history and the general medical knowledge in a unified graph structure.

![Report](VLM_final_report.pdf)
![Code](graph_creation.ipynb)


This research, conducted under the supervision of Prof. Galeotti at the RI, CMU, investigates methods to enhance VLMs, such as DINOv2, through the integration of Knowledge Graphs and Retrieval-Augmented Generation (RAG). The objective is to improve the automated assessment of patient vital signs as part of the DARPA-funded project.

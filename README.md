# REDOSE: Benchmark for Drug related entities extraction from Reddit

## Abstract

Physicians often learn about the effects of illicit drugs when users require emergency medical attention after an overdose, creating a knowledge gap in drug usage and effects between healthcare providers and patients. Some drug users share their experience of use online in a narrative-free text format, providing a complementary source of information that better represents general trends. Existing datasets for named entity recognition of drug names focus primarily on prescription medications and overlook slang or deliberately obscure mentions, such as “dope” for heroin or “fetty” for fentanyl. In addition, there are no standards for evaluating different approaches in this domain. Addressing this limitation, we introduce REDOSE (REddit Drug DOSe and Effect), which comprises 6,435 unique Reddit posts or comments related to substance abuse, annotated by physicians for drug names, effects, and doses. We report the performance of BERT-based models and state-of-the-art Large Language Models (i.e., GPT-4, Llama-3). REDOSE contributes to the literature by providing a patient-curated data set to guide and evaluate the development of algorithms that extract medically relevant information from unstructured texts. 

## Data

The dataset is split into 6,068 documents for training and 367 for testing. 

|          | Training | Test  |  Total |
|----------|:--------:|-------|:------:|
| Document |    6,068 |   367 |  6,435 |
| Sentence |   14,260 | 1,209 | 15,469 |
| Entity   |          |       |        |
| Drug     |    4,004 |   833 |  4,784 |
| Effect   |      674 |   128 |    750 |
| Dose     |      647 |    98 |    733 |

While annotations can be represented in various formats, we used the [BioC](https://pubmed.ncbi.nlm.nih.gov/24048470/) XML format due to several considerations. The format is simple and easy to modify, allowing additional analysis tools to be applied rapidly as needed.

In short, the starting point for the BioC format is a `collection` of documents. Each `document` consists of a series of passages. Every `passage` includes an `offset`, which suggests the character offset within the parent document, and `text`, which stores the actual text of the passage. In each passage, annotations, which identify entities of DRUG, EFFECT, and DOSE, are applied directly to the surface `text`. The annotation contains `location`, which details the starting `offset` attribute and the `length` of the annotated text within the passage.

## Acknowledgements

This work was supported by the National Library of Medicine [grant number R01LM014306], the NSF [grant number 2145640]. This study was supported by funding from the Artificial Intelligence/Machine Learning Consortium to Advance Health Equity and Researcher Diversity (AIM-AHEAD), a program of the National Institutes of Health (1OT2OD032581-02-259).

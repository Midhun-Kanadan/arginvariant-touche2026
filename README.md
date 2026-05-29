# arginvariant-touche2026

This repository contains the dataset-specific prompts for the system described in:

> **arginvariant at Touché 2026: Error-Driven Prompt Refinement for Argument Identification**
> Midhun Kanadan, Maximilian Heinrich, Benno Stein

## Shared Task

[Touché 2026 — Shared Task: Generalizability of Argument Identification in Context](https://touche.webis.de/clef26/touche26-web/generalizable-argument-mining.html)

The task evaluates cross-domain argument identification across ten benchmark corpora and three out-of-domain Twitter variants (TACO, TAPE, TAUS) annotated under different guidelines.

## Prompts

The `prompts/` directory contains the initial (v1) and final (best) prompt for each of the 13 corpora used in the evaluation. Each prompt encodes the annotation criteria of the respective corpus as a natural-language classification procedure.

| Corpus | Domain | Initial | Final |
|--------|--------|---------|-------|
| ABSTRCT | Biomedical abstracts | ABSTRCT1.txt | ABSTRCT5.txt |
| ACQUA | Comparative web sentences | ACQUA1.txt | ACQUA5.txt |
| AEC | Online debate forums | AEC1.txt | AEC5.txt |
| AFS | Structured debate platforms | AFS1.txt | AFS4.txt |
| ARGUMINSCI | Scientific publications | ARGUMINSCI1.txt | ARGUMINSCI3.txt |
| FINARG | Financial earnings calls | FINARG1.txt | FINARG6.txt |
| IAM | Heterogeneous web sources | IAM1.txt | IAM5.txt |
| PE | Persuasive essays | PE1.txt | PE6.txt |
| SCIARK | Scientific abstracts (SDGs) | SCIARK1.txt | SCIARK6.txt |
| USELEC | US presidential debates | USELEC1.txt | USELEC5.txt |
| TACO | Twitter (inference vs. information) | TACO1.txt | TACO3.txt |
| TAPE | Twitter (Persuasive Essay guidelines) | TAPE1.txt | TAPE3.txt |
| TAUS | Twitter (US debate guidelines) | TAUS1.txt | TAUS3.txt |

The version number in the filename indicates how many refinement iterations were applied. All prompts include a `{sentence}` placeholder substituted at inference time.

## System

The system applies iterative error-driven prompt refinement: an inner loop aggregates misclassification patterns shared across multiple LLMs on the training set and updates the prompt with targeted rules; an outer loop validates each revision on the development set and stops when Macro F₁ no longer improves. Final prompts are applied at inference time without any parameter updates.

The best submitted run achieved a Main Macro F₁ of **0.7834**, placing **second on the official leaderboard**.


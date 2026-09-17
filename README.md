# TalkFa: A Unified Benchmark for Farsi Dialogue Generation and Understanding

**TalkFa** is a unified benchmark for evaluating dialogue generation and
understanding in Farsi (Persian).

It brings together three complementary dialogue datasets covering
knowledge-grounded generation, dialogue-act classification, emotion
recognition, and sentiment analysis.

TalkFa was designed to support reproducible research on conversational AI
for Farsi, a language that remains substantially underrepresented in
dialogue research.

## 📚 Datasets

| Dataset | Dialogues | Turns | Task |
|---|---:|---:|---|
| **Wiki-FaDial** | 4,184 | 25,104 | Knowledge-grounded dialogue generation |
| **DailyDialog-FA** | 6,599 | 52,018 | Dialogue-act & emotion classification |
| **PlayDial-FA** | 2,070 | 16,499 | Dialogue-level sentiment classification |

In total, TalkFa contains approximately **12.9K dialogues** across three
different conversational settings.

### Wiki-FaDial

Wiki-FaDial contains **4,184 six-turn Farsi dialogues** grounded in
Wikipedia paragraphs.

Each dialogue is associated with its source paragraph and is designed to
remain semantically faithful to the source while using natural,
conversational Farsi.

Every generated dialogue was reviewed and revised by native Farsi
speakers.

**Task:** Knowledge-grounded dialogue generation.

### DailyDialog-FA

DailyDialog-FA is a culturally localized Farsi counterpart of DailyDialog.

It contains **6,599 dialogues and 52,018 turns**, with turn-level
annotations for:

**Dialogue acts**
- Inform
- Question
- Directive
- Commissive

**Emotions**
- Anger
- Disgust
- Fear
- Happiness
- Sadness
- Surprise
- No emotion

The dialogues were translated and culturally adapted into natural spoken
Farsi and subsequently reviewed by native Farsi speakers.

**Tasks:** Dialogue-act classification and emotion recognition.

### PlayDial-FA

PlayDial-FA contains **2,070 multi-turn dialogues** derived from
public-domain Farsi theatrical works.

The dialogues are annotated at the dialogue level with three sentiment
classes:

- Negative
- Neutral
- Positive

The corpus provides a more expressive conversational setting containing
rhetorical language, emotional expression, and stylistic variation.

**Task:** Dialogue-level sentiment classification.

## 🧑‍💻 Human-Curated Dataset Construction

TalkFa uses an **LLM-assisted, human-curated** construction pipeline.

LLMs were used during different stages of dataset construction, including
dialogue generation, translation, segmentation, and reformulation.
However, the resulting dialogues underwent multi-stage review and
revision by native Farsi speakers.

Only the final human-approved versions are included in the released
benchmark.

Independent external validation further evaluates the linguistic quality
and reproducibility of the annotations.

## 🤖 Models and Baselines

The benchmark evaluates instruction-tuned LLMs from the **Llama** and
**Mistral** families under zero-shot and LoRA-adapted settings.

The experiments include models ranging from **1B to 24B parameters**.

For classification, TalkFa additionally evaluates Farsi-specific and
multilingual encoders, including:

- FaBERT
- ParsBERT
- multilingual E5
- mBERT
- XLM-R
- RoBERTa

## 📊 Main Results

The experiments show that parameter-efficient adaptation substantially
improves performance across TalkFa.

Some of the main findings are:

- **FaBERT** achieves **0.75 macro-F1** on dialogue-act classification.
- **LoRA-Mistral-7B** reaches **0.38 macro-F1** on emotion recognition.
- **LoRA-Mistral-24B** achieves **0.62 macro-F1** on sentiment classification.
- Using only **25–50% of the Wiki-FaDial training data** recovers more than
  **90% of the final generation gains**.
- Human evaluation shows that high automatic generation scores do not
  necessarily correspond to highly natural dialogue.

In particular, the strongest evaluated generation model receives only
**2.74/5** in human evaluation despite achieving very high semantic
similarity scores.

These results highlight both the usefulness and the remaining difficulty
of Farsi dialogue modeling.

## 🔬 Tasks

TalkFa supports four primary research tasks:

1. Knowledge-grounded Farsi dialogue generation
2. Dialogue-act classification
3. Emotion recognition
4. Dialogue-level sentiment classification

The benchmark can also be used to study parameter-efficient adaptation,
low-resource learning, multilingual transfer, and dialogue evaluation.

## 📁 Repository Structure

```text
TalkFa/
├── data/
│   ├── wiki_fadial/
│   ├── dailydialog_fa/
│   └── playdial_fa/
├── annotation_guidelines/
├── src/
│   ├── generation/
│   ├── classification/
│   └── evaluation/
├── scripts/
├── results/
└── assets/

##reference
@article{jamshidi2026talkfa,
  title   = {TalkFa: A Unified Benchmark for Farsi Dialogue Generation and Understanding},
  author  = {Jamshidi, Neda and Zeinalipour, Kamyar and Akbari, Fahimeh
             and Bianchini, Monica and Maggini, Marco and Gori, Marco},
  year    = {2026},
  journal = {arXiv preprint arXiv:2609.01810}
}

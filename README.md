# Cross-Lingual Sentiment and Intent Classification for Indian Languages

Project 3: a multilingual NLU system that predicts sentiment and intent for
Hindi, Bengali, Marathi and Assamese text, designed to run on free-tier GPUs
(Kaggle/Colab).

**Status:** Week 1 (data curation and preprocessing) complete.
Next: Week 2 (model selection and baseline training).

## Datasets

| Dataset | Used for |
|---|---|
| IndicSentiment | Sentiment labels (human-annotated reviews) |
| Samanantar | Intent labels (rule-labeled English side, projected to the translation) |
| IndicCorpV2 | Unlabeled text for tokenizer analysis |

All datasets are from AI4Bharat and are used for research purposes only
(Samanantar is CC BY-NC 4.0).

## How to run

1. Open `notebooks/week1_data_curation.ipynb` on Kaggle with **Internet: On**.
2. Optional: add a Hugging Face token as a Kaggle secret named `HF_TOKEN` to
   avoid download rate limits.
3. Run all cells. Outputs are saved to `/kaggle/working/data`.

## Week 1 results

Tokenizer fertility (subword tokens per word; lower is better):

| Language | MuRIL | XLM-R |
|---|---|---|
| Hindi | 1.11 | 1.31 |
| Bengali | 1.23 | 1.79 |
| Marathi | 1.35 | 1.67 |
| Assamese | 1.42 | 2.56 |

MuRIL splits words less in every language. Fertility is only a proxy, so the
final model choice will be confirmed by F1 in Week 2.

## Known limitations

- Sentiment data is binary (no neutral class).
- Intent labels are rule-based (silver, not human-annotated); a manual audit
  is planned.
- Intent classes are balanced by capping, unlike the real distribution.
- Intent text is translated news while sentiment text is product reviews
  (domain mismatch).

# 📆 Attention-based Date Format Translation

This project implements a sequence-to-sequence (seq2seq) model with attention to convert human-readable dates (e.g., "21th of August 2016") into machine-readable formats (e.g., "2016-08-21"). Built using TensorFlow/Keras, this is a practical application of Neural Machine Translation (NMT) techniques.

---

## 📂 Dataset

- **Size:** 10,000 examples (generated)
- **Source Format:** Varied (natural language dates)
- **Target Format:** YYYY-MM-DD (machine format)
- **Preprocessing:** One-hot encoding, character-level vocabulary mapping

---

## 🧠 Model Architecture

- **Input:** 30-character one-hot encoded vectors
- **Encoder:** Bidirectional LSTM (Tx = 30)
- **Attention Layer:** Custom attention mechanism that aligns decoder state with encoder output
- **Decoder:** LSTM with 64 hidden units
- **Output:** Sequence of 10 softmax layers (Ty = 10), one for each character in the target date

---

## 🔧 Training Details

- **Loss:** Categorical Crossentropy
- **Optimizer:** Adam (`lr=0.005`, `beta_1=0.9`, `beta_2=0.999`, `decay=0.01`)
- **Metrics:** Accuracy
- **Batch Size:** 100
- **Epochs:** 1 (can be increased for better performance)

---

## ✅ Evaluation

Example conversions using the trained model:

| Input                  | Output      |
|------------------------|-------------|
| `3 May 1979`           | `1979-05-03` |
| `21th of August 2016`  | `2016-08-21` |
| `Tue 10 Jul 2007`      | `2007-07-10` |
| `March 3rd 2001`       | `2001-03-03` |
| `Saturday May 9 2018`  | `2018-05-09` |

---

## 🧪 Usage

- **Translate a date:** Use `translate_date("4th of July 2001")` to convert.
- **Visualize Attention:** Use `plot_attention_map(...)` to inspect attention weights.

---

## 📦 Dependencies

- `tensorflow`, `keras`
- `numpy`, `matplotlib`
- `faker`, `babel`, `tqdm`
- Custom utils: `nmt_utils.py`

---

## 📌 Notes

- The model supports a wide variety of date formats.
- It is trained end-to-end with attention from scratch or using pretrained weights.
- Extensible to other character-level NMT problems.

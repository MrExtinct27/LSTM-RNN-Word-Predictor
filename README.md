# 🔮 Next Word Prediction using LSTM (Hamlet Text)

This project is a deep learning application that predicts the **next word** in a sentence using an LSTM-based neural network trained on **Shakespeare's Hamlet**. It uses **NLTK for text loading**, **TensorFlow/Keras for training**, and is deployed using **Streamlit** for a real-time prediction interface.

👉 **Live Demo**: *Coming soon (deploy to Streamlit Cloud)*

---

## 📚 Dataset

We use the `shakespeare-hamlet.txt` text from the **NLTK Gutenberg corpus**:

- Downloaded using `nltk.download('gutenberg')`
- Text preprocessed to lowercase and tokenized
- Converted into input sequences for next-word prediction

---

## 🧠 Model Architecture

A **multi-layer LSTM** model with dropout was used to learn word dependencies.

```
Input (Padded Sequences)
   ↓
Embedding Layer
   ↓
LSTM Layer (150 units, return_sequences=True)
   ↓
Dropout Layer (0.2)
   ↓
LSTM Layer (100 units)
   ↓
Dense Layer with Softmax (output: vocabulary size)
```

- **Loss**: categorical crossentropy
- **Optimizer**: Adam
- **EarlyStopping**: Stops training if validation loss doesn’t improve for 3 epochs

---

## 🧪 Preprocessing Steps

- Tokenized entire Hamlet text using `Tokenizer` from Keras
- Created n-gram input sequences from lines
- Used `pad_sequences` to ensure consistent input shape
- One-hot encoded the output labels using `to_categorical`

---

## 📊 Training Performance

- Trained over 50 epochs
- Accuracy improved steadily, but model overfits if early stopping is not used
- Vocabulary size: ~4800 words
- Final model size: ~4.6MB

---

## 🚀 Streamlit App

The Streamlit app takes a partial sentence and predicts the **next likely word**.

### Example

```
Input:  To be or not to
Output: considered
```

### Run it locally:

```bash
streamlit run app.py
```

---

## 📦 Files in This Project

```
.
├── hamlet.txt                  # Raw Shakespeare data
├── next_word_lstm.h5           # Trained LSTM model
├── tokenizer.pickle            # Tokenizer used during training
├── app.py                      # Streamlit app
├── README.md                   # This file
├── requirements.txt            # Python dependencies
├── .gitignore
```

---

## 📄 requirements.txt (sample)

```
tensorflow==2.15.0
numpy
nltk
streamlit
scikit-learn
```

---

## 🔧 How to Use

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/next-word-lstm-hamlet.git
cd next-word-lstm-hamlet
```

### Step 2: Create a Virtual Environment (Python 3.11 recommended)

```bash
python3.11 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Run Streamlit App

```bash
streamlit run app.py
```

---

## ✨ Highlights

- Based on **Hamlet**, not modern data → interesting and poetic predictions!
- Uses LSTM for learning temporal patterns in word sequences
- Live prediction with **real-time inference**
- Easily extendable to any other text corpus (news, lyrics, articles)

---

## 🙏 Credits

- Shakespeare’s Hamlet text from [NLTK Gutenberg Corpus](https://www.nltk.org/)
- TensorFlow/Keras for modeling
- Streamlit for UI

---

## 🏁 License

MIT License. Free to use and modify for educational and commercial purposes.

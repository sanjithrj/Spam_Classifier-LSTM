# 🛡️ Spam Classifier using LSTM

A deep learning-based text classification system that identifies spam messages using Long Short-Term Memory (LSTM) neural networks. Built with PyTorch, this project achieves up to **96% accuracy** on SMS spam detection.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

---

## 🔍 Overview

Spam messages pose significant security risks and reduce user trust in digital communication. Traditional rule-based filters often struggle to adapt to evolving spam patterns. This project leverages LSTM networks, a type of Recurrent Neural Network (RNN), to effectively handle sequential text data and classify messages as either **Spam** or **Ham** (legitimate messages).

### Problem Statement

Develop an AI-powered system capable of:
- ✅ Automatically classifying text messages as Spam or Ham
- ✅ Handling variable-length message inputs
- ✅ Achieving high accuracy and robust generalization

---

## ✨ Features

- **LSTM-based Architecture**: Leverages Long Short-Term Memory networks for superior sequential pattern recognition
- **Custom Text Processing Pipeline**: Includes tokenization, vocabulary building, and sequence padding
- **High Accuracy**: Achieves up to 96% classification accuracy on test data
- **Easy Training & Inference**: Simple command-line interface for both training and prediction
- **Pre-trained Model**: Includes a ready-to-use trained model (`spamham_lstm.pt`)
- **Flexible Input Handling**: Supports both CSV and tab-separated data formats

---

## 📊 Dataset

- **Source**: SMS Spam Collection Dataset (`spamhamdata.csv`)
- **Format**: Tab-separated values with two columns:
  - Column 1: Label (`spam` or `ham`)
  - Column 2: Message text
- **Size**: Contains thousands of labeled SMS messages
- **Split**: 80% training, 20% testing

### Data Preprocessing

The preprocessing pipeline includes:
1. **Lowercasing**: Converts all text to lowercase
2. **Cleaning**: Removes non-alphanumeric characters
3. **Tokenization**: Splits text into individual words
4. **Vocabulary Building**: Creates a custom vocabulary from training data (minimum frequency: 2)
5. **Sequence Encoding**: Converts text to integer sequences
6. **Padding/Truncating**: Standardizes sequences to maximum length of 50 tokens

---

## 🏗️ Model Architecture

The spam classifier uses a deep learning architecture built with PyTorch:

```
Input Text → Embedding Layer → LSTM Layer → Fully Connected Layer → Output (Spam/Ham)
```

### Architecture Details

| Layer | Type | Parameters |
|-------|------|------------|
| **Embedding** | `nn.Embedding` | `vocab_size × 64` dimensions |
| **LSTM** | `nn.LSTM` | 64 input → 128 hidden units |
| **Fully Connected** | `nn.Linear` | 128 → 2 classes (spam/ham) |

### Training Configuration

- **Optimizer**: Adam (learning rate: 0.001)
- **Loss Function**: CrossEntropyLoss
- **Batch Size**: 32
- **Epochs**: 5
- **Max Sequence Length**: 50 tokens
- **Minimum Token Frequency**: 2

---

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sanjithrj/Spam_Classifier-LSTM.git
   cd Spam_Classifier-LSTM
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   Required packages:
   - `torch`: PyTorch deep learning framework
   - `pandas`: Data manipulation and analysis
   - `scikit-learn`: Train/test splitting utilities

---

## 💻 Usage

### Training the Model

To train the LSTM model from scratch:

```bash
python main.py
```

**Expected Output**:
```
Epoch 1: Train Loss=0.3901, Test Acc=0.9166
Epoch 2: Train Loss=0.1520, Test Acc=0.8861
Epoch 3: Train Loss=0.1492, Test Acc=0.9318
Epoch 4: Train Loss=0.1263, Test Acc=0.9641
Epoch 5: Train Loss=0.2000, Test Acc=0.9094
Model saved to spamham_lstm.pt
```

The trained model will be saved as `spamham_lstm.pt`.

### Running Inference

To classify messages using the trained model:

```bash
python inference.py
```

**Example Output**:
```
Text: Free entry in 2 a wkly comp to win FA Cup final tkts...
Predicted: spam

Text: Ok lar... Joking wif u oni...
Predicted: ham

Text: WINNER!! As a valued network customer you have been selected...
Predicted: spam
```

---

## 📈 Results

### Performance Metrics

- **Test Accuracy**: Up to **96.41%** (Epoch 4)
- **Training Loss**: Decreased from 0.3901 to 0.1263 over 5 epochs
- **Model Size**: Lightweight and efficient for deployment

### Sample Predictions

| Message | True Label | Predicted Label | ✅/❌ |
|---------|------------|-----------------|-------|
| "Free entry to win £900 prize..." | Spam | Spam | ✅ |
| "Are we meeting today?" | Ham | Ham | ✅ |
| "URGENT! You have won..." | Spam | Spam | ✅ |
| "I'm gonna be home soon..." | Ham | Ham | ✅ |

---

## 📁 Project Structure

```
Spam_Classifier-LSTM/
│
├── main.py                 # Training script
├── inference.py            # Inference/prediction script
├── model.py                # LSTM model architecture definition
├── data_utils.py           # Data preprocessing utilities
├── requirements.txt        # Python dependencies
├── spamhamdata.csv         # SMS spam dataset
├── spamham_lstm.pt         # Pre-trained model weights
└── README.md               # Project documentation
```

### File Descriptions

- **`main.py`**: Handles data loading, model training, and evaluation
- **`inference.py`**: Loads the trained model and performs predictions on the dataset
- **`model.py`**: Defines the `SpamHamLSTM` PyTorch model class
- **`data_utils.py`**: Contains utilities for tokenization, vocabulary building, and dataset creation
- **`spamhamdata.csv`**: Tab-separated dataset with spam/ham labels and message text
- **`spamham_lstm.pt`**: Saved model state dictionary (trained weights)

---

## 🤝 Contributing

Contributions are welcome! To contribute to this project:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Make your changes and commit them (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### Suggestions for Improvement

- Add support for real-time single message prediction
- Implement cross-validation for robust evaluation
- Experiment with different architectures (GRU, Transformer)
- Add a web interface for easy interaction
- Implement confusion matrix and detailed metrics reporting

---

## 📄 License

This project is open source and available for educational and research purposes.

---

## 🙏 Acknowledgments

- Dataset: [SMS Spam Collection Dataset](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection)
- Built with [PyTorch](https://pytorch.org/)
- Inspired by advances in natural language processing and deep learning

---

**Made with ❤️ by [Sanjith RJ](https://github.com/sanjithrj)**

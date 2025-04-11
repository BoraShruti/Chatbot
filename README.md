
# Chatbot TorchScript Profiler

**Author:** Your Name or Organization  
**Date:** _Automatically generated (e.g., today's date)_

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Architecture](#architecture)
- [Training](#training)
- [Evaluation & Inference](#evaluation--inference)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Overview

The project is based on PyTorch and implements a sequence-to-sequence chatbot using an encoder–decoder architecture with Luong attention and integrated TorchScript profiling.

It includes routines for data preprocessing, vocabulary construction, model definition, training (with teacher forcing), checkpointing, and evaluation/inference. 
---

## Features

- **Sequence-to-Sequence Chatbot:** Uses a bidirectional GRU-based encoder and an attention-based decoder (Luong attention).
- **Data Preprocessing and Vocabulary Building:** Downloads a movie corpus using Convokit, extracts dialogue pairs, and normalizes text.
- **Training Pipeline:** Implements teacher forcing, gradient clipping, and checkpoint saving.
- **Model Profiling:** Integrates TorchScript profiling tools to analyze performance.
- **Interactive Inference:** Provides an interactive interface for chatting with the trained model.

---



### Clone the Repository

```bash
git clone https://github.com/yourusername/Chatbot_TorchScript_Profiler.git
cd Chatbot_TorchScript_Profiler
```

### Install Dependencies

Install the required Python libraries:

Sample `requirements.txt`:

```text
torch>=1.10.0
convokit
matplotlib
```

Then install:

```bash
pip install -r requirements.txt
```

### Google Colab Setup (Optional)

If you're using [Google Colab](https://colab.research.google.com), upload the notebook `Chatbot_Torchscript_Profiler.ipynb` and mount Google Drive if you want to persist data.

---

## Usage

### Data Download and Preprocessing

The notebook:
- Downloads the movie corpus via Convokit.
- Extracts input–response dialogue pairs.
- Normalizes and cleans the text.
- Writes formatted data to `formatted_movie_lines.txt`.

### Training the Model

- The model uses an encoder and Luong attention-based decoder.
- Training supports teacher forcing and gradient clipping.
- Periodic checkpointing saves model weights and states.

### Inference

Includes a greedy search decoder for real-time interaction.

### Profiling and Analysis

Uses TorchScript profiling tools to measure and improve model performance.

---

## Architecture

### Encoder

`EncoderRNN` is a bidirectional GRU that outputs hidden state representations. Forward and backward outputs are summed into a unified representation.

### Attention Mechanism

`Attn` class implements **Luong Attention**, with modes:
- **Dot**
- **General**
- **Concat**

### Decoder

`LuongAttnDecoderRNN` uses attention to compute context vectors and generate output tokens one by one.

---

## Training

### Loss Computation

A masked **negative log-likelihood (NLL)** loss ignores padding tokens during training.

### Teacher Forcing

Randomly uses the true previous token as the decoder input to stabilize learning.

### Checkpointing

Saves:
- Model weights
- Optimizer state
- Vocabulary

To resume or evaluate later.

### Gradient Clipping

Prevents exploding gradients by bounding updates.

---

## Evaluation & Inference

### Greedy Search Decoder

Decodes token-by-token, selecting the highest-probability token at each step.

### Interactive Mode

`evaluateInput()` enables a conversational loop to chat with the model.

---

## Contributing

Contributions are welcome! Here's how to help:

- Fork the repository
- Submit pull requests
- Follow existing coding conventions
- Document your changes clearly
- Add tests if applicable

---

## Acknowledgements

- [PyTorch](https://pytorch.org/) for the deep learning framework
- [Convokit](https://github.com/CornellNLP/convokit) for conversational datasets
- The original PyTorch tutorials for inspiration


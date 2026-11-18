# StoryGPT – AI Story Generator

StoryGPT is a character-level language model built using a decoder-only Transformer architecture. It learns patterns from simple English stories in the TinyStories dataset and generates new story-like text one character at a time.

The model is implemented and trained completely from scratch using PyTorch, without pretrained model weights or external AI APIs.

## Project Overview

The objective of this project is to understand and implement the fundamental concepts behind GPT-style language models, including tokenization, embeddings, self-attention, Transformer blocks, model training, evaluation and text generation.

## Key Features

- Custom character-level tokenizer
- Randomly initialized neural network parameters
- Decoder-only Transformer architecture
- Multi-head causal self-attention
- Positional embeddings
- Feed-forward neural networks
- Residual connections and layer normalization
- Model training using AdamW optimizer
- Training and validation loss evaluation
- Temperature-based text generation
- Model checkpoint saving and loading

## Dataset

**Dataset:** TinyStories

The model is trained on a subset of TinyStories, a dataset containing short stories written in simple English. It is designed to help language models learn basic language patterns and story structures.

Dataset source:  
https://huggingface.co/datasets/roneneldan/TinyStories

Dataset split:
- Training data: 20,000 stories
- Validation data: 2,000 stories
- Total: 22,000 stories

The selected stories are combined into text sequences and processed using character-level tokenization.

## Model Architecture

| Parameter | Configuration |
|---|---:|
| Model type | Decoder-only Transformer |
| Tokenization | Character-level |
| Vocabulary size | 98 |
| Embedding dimension | 128 |
| Attention heads | 4 |
| Transformer blocks | 4 |
| Context length | 128 |
| Batch size | 32 |
| Dropout | 0.1 |
| Trainable parameters | 767,330 |
| Optimizer | AdamW |
| Learning rate | 0.0003 |
| Training iterations | 3,000 |

## Model Architecture Flow

1. Input text
2. Character-level tokenization
3. Token embeddings
4. Positional embeddings
5. Four stacked Transformer blocks, each containing:
   - Multi-head causal self-attention
   - Residual connection and layer normalization
   - Feed-forward neural network
   - Residual connection and layer normalization
6. Final layer normalization
7. Language model output layer
8. Next-character prediction

## Training Results

Final recorded evaluation:

| Metric | Result |
|---|---:|
| Final training loss | 1.1331 |
| Final validation loss | 1.1413 |
| Training iterations | 3,000 |
| Training time | Approximately 83.4 seconds |
| Training hardware | NVIDIA T4 GPU |

The decreasing training and validation losses indicate that the model learned character and language patterns from the TinyStories dataset. The small difference between the two losses suggests similar performance on the training and validation data.

## Text Generation

StoryGPT generates text by predicting one character at a time based on the preceding characters.

It supports:
- User-provided text prompts
- Configurable generation length
- Temperature

**Note:** StoryGPT is an educational language-model implementation, not a reproduction of OpenAI's GPT models.

# StoryGPT – AI Story Generator

StoryGPT is a character-level language model built using a decoder-only Transformer architecture. It learns patterns from Shakespeare's text and generates new text one character at a time.

The model is implemented and trained completely from scratch using PyTorch, without pretrained model weights or external AI APIs.

## Project Overview

The objective of this project is to understand and implement the fundamental concepts behind GPT-style language models, including tokenization, embeddings, self-attention, Transformer blocks, model training and text generation.

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

**Dataset:** Tiny Shakespeare

The model is trained on a text corpus containing approximately 1.1 million characters from Shakespeare's works.

Dataset source:
https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt

Dataset split:
- Training data: 90%
- Validation data: 10%

## Model Architecture

| Parameter | Configuration |
|---|---:|
| Model type | Decoder-only Transformer |
| Tokenization | Character-level |
| Vocabulary size | 65 |
| Embedding dimension | 128 |
| Attention heads | 4 |
| Transformer blocks | 4 |
| Context length | 128 |
| Dropout | 0.1 |
| Trainable parameters | 758,849 |
| Optimizer | AdamW |
| Learning rate | 0.0003 |
| Training iterations | 3,000 |

## Model Architecture Flow

1. Input text
2. Character-level tokenization
3. Token embeddings
4. Positional embeddings
5. Multi-head causal self-attention
6. Feed-forward neural network
7. Residual connections and layer normalization
8. Four stacked Transformer blocks
9. Final layer normalization
10. Language model output layer
11. Next-character prediction

## Training Results

Final recorded evaluation:

| Metric | Result |
|---|---:|
| Initial training loss | 4.1710 |
| Final training loss | 1.4258 |
| Final validation loss | 1.6277 |
| Training iterations | 3,000 |

The decreasing training and validation losses indicate that the model learned character and language patterns from the training corpus.

## Text Generation

StoryGPT generates text by predicting one character at a time.

It supports:
- User-provided text prompts
- Configurable generation length
- Temperature-based sampling

Example prompt:

`Once upon a time`

The generated text follows patterns learned from Shakespeare's writing. Since this is a relatively small character-level model, generated text may contain grammatical errors, repetitions and incomplete sentences.

## Technologies Used

- Python
- PyTorch
- NumPy
- Matplotlib
- Google Colab
- Git and GitHub

## How to Run

1. Clone or download this repository.
2. Open `StoryGPT.ipynb` in Google Colab.
3. Select a GPU runtime if available.
4. Run the notebook cells in order.
5. The notebook downloads the dataset and prepares the tokenizer.
6. Build and train the Transformer model.
7. Generate text using custom prompts.

The saved checkpoint can also be loaded to reuse the trained model without repeating training.

## Project Structure

```text
StoryGPT/
│
├── StoryGPT.ipynb
├── storygpt_checkpoint.pth
├── README.md
├── requirements.txt
│
└── screenshots/
    ├── training_loss.png
    └── generated_story.png
```

## Limitations

- Character-level rather than word-level or subword tokenization.
- Relatively small model size.
- Training corpus is limited to Shakespeare's text.
- Generated text is not guaranteed to be grammatically correct or logically coherent.
- The model does not have external knowledge or real-world understanding.

## Future Improvements

- Experiment with larger Transformer architectures.
- Train for additional iterations and compare validation performance.
- Explore subword tokenization.
- Experiment with larger and more diverse text datasets.
- Improve text-generation quality and sampling strategies.

## Author

Developed as a hands-on deep learning project to understand and implement a GPT-style language model from scratch.

---

**Note:** StoryGPT is an educational language-model implementation, not a reproduction of OpenAI's GPT models.

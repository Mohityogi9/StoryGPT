# StoryGPT – AI Story Generator

StoryGPT is a character-level, decoder-only Transformer language model built from scratch using PyTorch. It is trained on a subset of the TinyStories dataset to learn patterns in short stories and generate new story-like text from a given prompt.

The main objective of this project is to understand the internal working of GPT-style language models, including tokenization, embeddings, causal self-attention, Transformer blocks, model training, checkpoint saving and loading, and text generation.

> **Note:** This is an educational project. The generated stories may contain grammatical errors, repetition, incomplete sentences, or unrelated ideas.

## Features

- Loads a subset of the TinyStories dataset.
- Implements character-level tokenization.
- Builds a GPT-style language model from scratch using PyTorch.
- Uses token embeddings and positional embeddings.
- Implements masked (causal) self-attention.
- Uses multi-head attention with 4 attention heads.
- Implements feed-forward neural networks.
- Uses residual connections and layer normalization.
- Trains the model using the AdamW optimizer.
- Evaluates training and validation loss.
- Generates text using temperature-based sampling.
- Saves the trained model in a checkpoint file.
- Supports loading a previously trained model without retraining.

## Dataset

The project uses the **TinyStories dataset** from Hugging Face.

Dataset: https://huggingface.co/datasets/roneneldan/TinyStories

The following subset was used:

| Dataset Split | Number of Stories |
|---|---:|
| Training | 20,000 |
| Validation | 2,000 |
| **Total** | **22,000** |

The stories are converted into a continuous text sequence, and the model learns to predict the next character.

## Model Architecture

StoryGPT uses a decoder-only Transformer architecture.

### Model Configuration

| Parameter | Value |
|---|---:|
| Tokenization | Character-level |
| Vocabulary Size | 98 |
| Batch Size | 32 |
| Context Length | 128 |
| Embedding Dimension | 128 |
| Attention Heads | 4 |
| Transformer Layers | 4 |
| Feed-Forward Hidden Dimension | 512 |
| Dropout | 0.1 |
| Training Iterations | 3,000 |
| Learning Rate | 0.0003 |
| Optimizer | AdamW |
| Total Parameters | 767,330 |

### Architecture Workflow

1. **Input Text:** The model receives a sequence of characters.
2. **Character Tokenization:** Each character is converted into a numerical token.
3. **Token Embeddings:** Numerical tokens are converted into dense vector representations.
4. **Positional Embeddings:** Position information is added to token embeddings.
5. **Transformer Blocks:** The model processes the sequence through 4 Transformer blocks.
   - Masked Multi-Head Self-Attention
   - Residual Connections
   - Layer Normalization
   - Feed-Forward Neural Network
6. **Output Layer:** A linear layer predicts scores for the next character.
7. **Text Generation:** The model generates one character at a time using autoregressive sampling.

## Training and Evaluation

The model was trained for 3,000 iterations using an NVIDIA T4 GPU through Google Colab.

### Final Training Results

| Metric | Result |
|---|---:|
| Training Iterations | 3,000 |
| Training Loss | 1.1314 |
| Validation Loss | 1.1341 |
| GPU | NVIDIA T4 |
| Training Time (last 2,900 iterations) | Approximately 83.4 seconds |

The training and validation losses are close in this run, indicating similar loss values on the two dataset splits.

## Text Generation

StoryGPT generates story-like text based on user-provided prompts.

Example prompts:

- `Once upon a time`
- `One day, a little girl`
- `A little boy went to`
- `One sunny morning`

The project uses temperature-based sampling to control the randomness of generated text.

### Temperature Comparison

| Temperature | Behaviour |
|---|---|
| 0.5 | More predictable and comparatively readable output |
| 0.8 | More variation in generated text |
| 1.0 | More random and creative output |

In the experiments, temperature 0.5 produced the most readable results among the tested settings.

## Checkpoint Saving and Loading

After training, the model is saved in:

`StoryGPT_Final_Checkpoint.pth`

The checkpoint contains:

- Model weights (`model_state_dict`)
- Optimizer state (`optimizer_state_dict`)
- Vocabulary size
- Character vocabulary
- Character-to-index mapping (`stoi`)
- Index-to-character mapping (`itos`)
- Model configuration
- Final training loss
- Final validation loss

The notebook also includes code to reload the saved checkpoint.

This allows the trained model to be restored in a new Google Colab session without repeating all 3,000 training iterations.

To restore the model:

1. Run the cells that define the tokenizer and model architecture.
2. Create the model and optimizer.
3. Upload `StoryGPT_Final_Checkpoint.pth`.
4. Execute the checkpoint-loading cell.
5. Run the story-generation cells.

## Technologies Used

- Python
- PyTorch
- Hugging Face Datasets
- NumPy
- Matplotlib
- Google Colab
- CUDA
- Git and GitHub

## How to Run

### Using Google Colab

1. Open the StoryGPT notebook in Google Colab.
2. Select a GPU runtime for faster training.
3. Run the notebook cells in sequence.
4. The notebook downloads and prepares the TinyStories dataset.
5. The model is created and trained.
6. The final checkpoint is saved automatically.
7. Run the generation cells to generate stories using different prompts and temperatures.

## Project Structure

```text
StoryGPT/
│
├── StoryGPT.ipynb
├── StoryGPT_Final_Checkpoint.pth
├── README.md
└── requirements.txt
```

## Limitations

- Uses character-level tokenization instead of subword tokenization.
- Has a relatively small model architecture.
- Trained on only a subset of the TinyStories dataset.
- Generated text may contain grammatical errors and spelling mistakes.
- May produce repeated phrases or incomplete sentences.
- Does not always maintain logical consistency throughout a story.
- Does not use external knowledge or pretrained language model weights.

## Future Improvements

- Train on a larger dataset.
- Increase the number of Transformer layers and embedding dimensions.
- Experiment with subword tokenization.
- Add a dedicated end-of-story token.
- Experiment with different text-generation sampling strategies.
- Evaluate generated stories using suitable language-generation metrics.

---

This project was developed to explore and understand the fundamentals of GPT-style language models and Transformer-based text generation by implementing a small language model from scratch.




# Week 3 — Notes
Simple notes in my own words 

---

##  1. Why Transformers?

Before Transformers, models like RNN, LSTM, and GRU processed text one word at a time.  
These models had problems:
- They forget long-distance relationships
- They can’t compare all words together
- They are slow because they are sequential
- They don’t scale well

Transformers fix all of this because they:
- Process all words at the same time (parallel)
- Compare every word with every other word
- Handle long context easily
- Train faster and scale to huge models

This is why almost all modern NLP models (BERT, GPT, LLaMA, etc.) use Transformers.

---

##  2. What is Self-Attention?

Self-attention lets every word look at all other words and decide which ones matter.

Example:
“She was tired because **she** didn’t sleep.”

To understand the second “she,” the model needs to link it to the correct person.  
Self-attention learns these connections automatically.

### How it works (super simple):
- Each word asks: “Who is important for me?”
- Each word compares itself with all other words
- It gives an importance score to each word
- It builds a new meaning using the important words

This helps the model understand relationships across the entire sentence.

---

##  3. Q, K, V (Query, Key, Value)

Each word becomes three versions:
- **Query (Q):** what the word is looking for
- **Key (K):** what information the word contains
- **Value (V):** the actual meaning the word carries

Attention = matching Q of one word with K of all other words.  
The better the match → the higher the attention.

---

##  4. Why Softmax?

Softmax converts attention scores into:
- probabilities
- numbers between 0 and 1
- total sum = 1

This lets the model focus on the important words and ignore the rest.

---

##  5. Multi-Head Attention (MHA)

One attention pattern is not enough because language has many types of relationships.

Multi-Head Attention means:
- Many attention heads run in parallel
- Each head learns a different pattern

Examples:
- One head focuses on pronouns (he, she, it)
- One head focuses on verbs
- One head focuses on long-range dependencies
- One head focuses on adjectives
- One head focuses on sentence structure

After processing, all heads are combined to give a richer understanding.

---

##  6. Why Multi-Head Attention is powerful

- The model learns multiple meanings and patterns
- It understands context better
- It captures grammar + semantics
- It is more flexible and powerful than RNN/LSTM

MHA is one of the main reasons why Transformer models are so successful.

---

##  Summary (date :- 18/11/25)

- Transformers fix the limitations of RNN/LSTM
- Self-attention helps each word see the whole sentence
- Q, K, V help calculate which words matter
- Softmax turns attention into probabilities
- Multi-Head Attention gives multiple “views” of the text
- This combination makes Transformers extremely powerful


# Topic 4 — Transformer Encoder Architecture (21/11/25)

Simple notes in my own words.

---

## ⭐ What is a Transformer Encoder?

A Transformer encoder block has 5 main parts:
1. Input Embeddings  
2. Positional Encoding  
3. Multi-Head Self-Attention  
4. Feed-Forward Network (FFN)  
5. LayerNorm + Residual Connections  

These layers are stacked many times (e.g., BERT has 12–24 layers).

---

##  1. Input Embeddings

Words are turned into vectors using an embedding matrix.

Example:
"cat" → [0.23, -0.18, 0.91, ...]

Embeddings capture the meaning of words.

But embeddings don’t store word order, so we add positional encoding.

---

##  2. Positional Encoding (PE)

Transformers don’t know word order automatically.

PE adds position information like:
- first word  
- second word  
- third word  

Final input = embedding + positional vector

This helps the model understand structure and grammar.

---

##  3. Multi-Head Self-Attention

Already learned earlier:
- Each word looks at all other words
- Attention finds important relationships
- Multiple heads learn different patterns in parallel

Attention gives the encoder a deep understanding of context.

---

##  4. Feed-Forward Network (FFN)

After attention, each word vector goes through:
Linear → ReLU → Linear

This helps:
- Mix iormationnf
- Transform features
- Learn more complex patterns

This step is applied independently to each word vector.

---

##  5. LayerNorm + Residual Connections

### Residual Connections:
Output = input + layer_output  
This stabilizes training and prevents vanishing gradients.

### Layer Normalization:
Keeps values stable and avoids exploding gradients.

Both of these make Transformer training very stable even at huge depth.

---

##  Full Encoder Block Flow

Input  
→ Embedding  
→ Positional Encoding  
→ LayerNorm  
→ Multi-Head Attention  
→ Residual Connection  
→ LayerNorm  
→ Feed-Forward Network  
→ Residual Connection  
→ Output

---

##  Why the Encoder is Powerful

- sees full context of a sentence  
- multiple heads learn multiple relationships  
- positional encoding gives order  
- residuals + layernorm stabilize training  
- can stack many layers for deep understanding  

DistilBERT is simply a smaller, faster version of the BERT encoder.

# Topic 5 — Tokenization (Notes)

Simple notes in my own words.

---

##  Why Tokenization is needed

Transformers cannot read raw text.  
They only understand numbers.  
So tokenization converts text → subwords → token IDs.

This step is critical for every Transformer model.

---

##  1. WordPiece (BERT / DistilBERT)

Breaks words into meaningful pieces.

Examples:
playing → play + ##ing  
unbelievable → un + believe + ##able

Helps with:
- rare words
- different word forms
- smaller vocabulary

---

##  2. BPE (Byte Pair Encoding) — used in GPT-2

Breaks text into frequent character pairs and merges them.

Examples:
international → inter + nation + al  
superstar → super + star

This allows GPT models to generate any kind of text.

---

##  3. Token IDs

After tokenizing, each word/subword becomes a number.

Example:
["this", "movie", "was"] → [2023, 4562, 923]

These IDs are what go into the embedding layer.

---

##  4. Special Tokens

[CLS] → start of sentence  
[SEP] → separator/end  
[PAD] → padding  
<|endoftext|> → GPT special token

Example BERT input:
[CLS] the movie was great [SEP]

---

##  5. Attention Mask

Tells the model which tokens to pay attention to.

Example:
Input:  [the, movie, was, PAD, PAD]  
Mask:   [1,   1,     1,   0,   0]

1 = real token  
0 = padding token

---

##  6. Padding & Truncation

All sequences must be the same length in a batch.

Short → padded  
Long → truncated

This makes batching efficient.

---

##  7. Tokenizer must match the model

The tokenizer and model are trained together.  
You should ALWAYS use the correct tokenizer for the model.  
A mismatched tokenizer ruins the output completely.

---

##  Summary

- Tokenization splits text into subwords  
- Converts them into numeric IDs  
- Adds special tokens  
- Creates attention masks  
- Handles padding and truncation  
- Tokenizer is a core part of the Transformer


# Topic 6 — HuggingFace Pipelines (Notes)

Simple notes in my own words.

---

##  What is a Pipeline?

A pipeline is a simple high-level tool that lets me run NLP models in one line.  
It automatically handles:
- tokenization
- padding and masks
- running the model
- decoding the output

I only give text → pipeline gives results.

---

##  Why Pipelines are useful

- Very easy to use  
- Great for testing and prototyping  
- No need to manually handle tokenizer or model  
- Lets me understand how a task works quickly  
- Good first step before fine-tuning any model

---

##  Common Pipeline Tasks

1. Sentiment analysis  
2. Text generation (GPT-2)  
3. Fill-mask  
4. Question answering  
5. Translation  
6. Summarization  
7. Named entity recognition  

Pipelines load the right model for the task automatically.

---

##  What Pipelines do internally

Given a text, pipelines:
1. Tokenize it  
2. Convert to token IDs  
3. Run it through the Transformer model  
4. Decode predictions into human-readable results  

Everything is abstracted away.

---

##  Why Pipelines come before fine-tuning

They help me:
- see how models behave
- quickly test ideas
- inspect outputs
- understand the task
- validate the environment (CPU/GPU)

This sets the foundation before training my own models.

---

##  Summary

- Pipelines make Transformers extremely easy to use  
- Perfect for quick experiments  
- Handle the full text → prediction workflow  
- Useful for many tasks (sentiment, generation, QA, etc.)  
- A great starting point before customizing or fine-tuning models



# Topic 7 — Fine-Tuning DistilBERT (Notes)

Simple notes in my own words.

---

##  What is Fine-Tuning?

Fine-tuning means taking a pretrained model (DistilBERT) and training it a little bit on my specific task (e.g., sentiment classification).

The model already knows language.  
I only teach it my task.

---

##  How DistilBERT is used for Classification

- Input passes through DistilBERT encoder
- I take the [CLS] token output
- A small classifier layer is added on top
- The classifier predicts the label (0/1)

This requires very little training because DistilBERT already understands English.

---

##  Why Fine-Tuning Works

DistilBERT already learned:
- grammar  
- meaning  
- context  
- relationships between words  
- world knowledge  

Fine-tuning only adjusts it slightly for my dataset.

---

##  What is needed before training

- tokenized text  
- attention masks  
- numeric labels  
- fixed max sequence length  
- matching tokenizer + model  

Everything must match DistilBERT’s training style.

---

##  Fine-Tuning Steps (Concept)

1. Tokenize dataset  
2. Add classification head  
3. Train model  
4. Evaluate results  
5. Save the model  

This is the basic workflow.

---

##  Loss Function

For classification tasks, DistilBERT uses **Cross-Entropy Loss**.

---

##  Important Hyperparameters

- learning rate: 2e-5 to 5e-5  
- batch size: 8 or 16  
- epochs: 2–3  
- weight decay: 0.01  

These values usually give excellent accuracy.

---

##  What Actually Gets Trained

### Full fine-tuning:
- all DistilBERT layers
- classifier head  
(Recommended)

### Partial fine-tuning:
- only classifier head  
(Faster but worse results)

---

##  Why Fine-Tuning is Valuable

Almost all NLP tasks today involve:
- BERT  
- DistilBERT  
- RoBERTa  
- GPT models  

Fine-tuning lets me adapt these huge models to ANY dataset.

---

##  Summary

- DistilBERT already knows language very well  
- Fine-tuning teaches it my specific labels  
- Very little data and compute needed  
- Extremely powerful for NLP applications  

# Topic 8 — GPT-2 Text Generation (Notes)

Simple notes in my own words.

---

##  What GPT-2 is

GPT-2 is a decoder-only Transformer model.  
It generates text by predicting the next token one by one.  
It only looks left-to-right (causal model).

---

##  How GPT-2 learns

GPT-2 is trained with language modeling:
Given some text, predict the next word.

Example:
Input: "The cat sat on the"  
Target: "mat"

Through this, it learns grammar, meaning, style, and long context.

---

##  Causal Self-Attention

GPT-2 uses masked attention:
Each token can only see previous tokens, not future ones.

This makes GPT good for prediction and generation.

---

##  Why GPT-2 is good for generation

- predicts next tokens naturally  
- keeps long-range context  
- learns writing style  
- no labels needed  
- easy to fine-tune  

It can generate stories, conversations, tweets, descriptions, poems, etc.

---

##  Tokenization in GPT-2 (BPE)

GPT-2 uses BPE (Byte Pair Encoding).  
This handles any text (normal words, code, emojis).

Example:
"transformers" → "transform" + "ers"

---

##  Sampling Methods

### Temperature:
low = predictable  
high = creative

### Top-K:
choose from top K tokens

### Top-P (nucleus):
choose from a set of tokens with total prob P

These control creativity vs accuracy.

---

##  Generation Flow

1. Tokenize prompt  
2. Feed to GPT-2  
3. Predict next token  
4. Append token  
5. Repeat until max length  

---

##  Summary

- GPT-2 is a decoder Transformer  
- Predicts next word (language modeling)  
- Uses causal self-attention  
- Great for text generation  
- Temperature, top-k, top-p control creativity  
- Easy to fine-tune for custom tasks  

# Topic 9 — End-to-End Transformer Workflow (Notes)

Simple notes in my own words.

---

##  1. Input Text
The user gives raw text.  
Transformers cannot read raw text, so tokenization is required.

---

##  2. Tokenization

The tokenizer converts text into:
- subword tokens  
- special tokens  
- token IDs (numbers)  
- attention masks  
- padding / truncation  

This prepares the input for the model.

---

##  3. Embedding Layer

Each token ID is turned into:
- word embedding  
- positional embedding  
- segment embedding (if needed)

These are added together to give meaning + position.

---

##  4. Transformer Blocks

Each block has:
- Multi-head self-attention  
- Add + LayerNorm  
- Feed-forward network  
- Add + LayerNorm again

These layers extract context and meaning across the whole sentence.

---

##  5. Output Representations

DistilBERT / BERT:
- use the [CLS] token for classification  
GPT-2:
- uses the last token hidden state to predict the next token.

---

##  6. Task Heads

### DistilBERT:
- classification head (linear layer + softmax)

### GPT-2:
- next-token prediction head
- repeated to generate long text

---

##  7. Final Outputs

Examples:
- Sentiment: "Positive (0.98 confidence)"  
- GPT-2: Generated text after the prompt  

---

##  8. Fine-Tuning Loop (Concept)

1. Forward pass  
2. Compute loss  
3. Backpropagate  
4. Update weights  
5. Repeat for all batches  

This adapts the pretrained model to my dataset.

---

##  9. Inference Flow

1. Tokenize input  
2. Convert to IDs + masks  
3. Model forward  
4. Decode predictions  
5. Return final text / label  

---

##  10. Summary

- Tokenizer prepares the text  
- Embeddings give meaning and position  
- Transformer layers analyze the sequence  
- Task heads make predictions  
- Fine-tuning makes the model task-specific  
- Inference follows the same pipeline without training  


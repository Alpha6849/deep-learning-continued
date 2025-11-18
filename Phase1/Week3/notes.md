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


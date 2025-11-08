# Week 1 — Sequence Models (RNN → LSTM → GRU) (will implement a text generator project to understand all 3)

## Day 1 Progress (8/11/25)
- Learned what sequential data is
- Understood why normal neural networks cannot remember order
- Understood RNN idea: carries memory from previous steps
- Learned that RNN forgets long-term info → leads to LSTM

## Key Understanding (In my own words)
Sequential data = data where ORDER matters.

RNN remembers previous words, but forgets long-term ones.

LSTM is like a “brain” that decides:
- what to remember
- what to forget
- what to output

RNN = Has memory, but forgets quickly.
LSTM = Better memory, remembers longer.
GRU = Faster version of LSTM.

Text is a sequence.
RNN remembers but forgets too soon.
LSTM remembers important things longer using gates.

LSTM :- Input  (40 characters) → Model → Output (next character)

Day 1 Progress:
- Learned what sequential text data is.
- Understood why RNN remembers short-term and LSTM remembers long-term.
- Prepared Shakespeare dataset.
- Created input-output sequence pairs.
- Built and trained LSTM model for 1 epoch.
- Successfully generated first Shakespeare-like text.

The model already learned:
- Naming and dialogue structure.
- Sentence rhythm and play formatting.
- Old-English style.

Tomorrow:
- Train for additional 5 epochs.
- Experiment with temperature = 0.3, 0.7, 1.2.
- Save generated samples.




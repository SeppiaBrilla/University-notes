They are a type of [[Recurrent neural networks]] that uses an LSTM layer to better process the sequences. The LSTM layer works with two different states:
- $h^{(t)}$ hidden state which stores short-term information 
- $c^{(t)}$ cell state which stores long-term information. The LSTM can read, write or erase information to the cell state.
Both states are of length $n$. 
The communication with the cell state is handled by three gates:
- Forget gate: which controls what should be kept and what should be forgotten and works as $f^{(t)} + \sigma \left( W_fh^{(t - 1)} + U_fx^{(t)} + b_f \right)$ 
- Input gate: which controls what part of the new content write to the cell state and works as $i^{(t)} = \sigma \left( W_ih^{(t - 1)} + U_ix^{(t)} + b_i \right)$
- Output gate: which controls what part of the cell state output to the hidden state and works as $i^{(t)} = \sigma \left( W_oh^{(t - 1)} + U_ox^{(t)} + b_o \right)$

The new content to be written to the cell state can be computed with the function $\tilde{c}^{(c)} = \tanh \left (W_c h^{(t - 1)} + U_cx^{(t)} +b_c \right)$. Then, some content gets erased from the cell state to make space for the new content with the function $c^{(t)} + f^{(t)} \times c^{(t - 1)} + i^{(t)} \times \tilde{c}^{(t)}$. The hidden state, then, read some content from the cell state using the function $h ^{(t)} = o^{(t)} \times \tanh c^{(t)}$. 
This type of layer does not guarantee to solve the vanishing gradient problem, however, it can help a lot with it.

## Gru

It is a simpler version of the LSTM layer with only one state, and the network can decide whether to write or not to that state. IT works with two gates:
- Update gate: which controls which part of the state to update or preserve 
- Reset gate which control which part of the previous state use in the current computation.
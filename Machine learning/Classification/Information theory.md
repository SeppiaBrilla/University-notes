it is primarly used in telecomunications, and it is based on the concept of _entropy_.

### Bit transmission example
Let's say we have 4 possible value and a probability distribution:
$$
P(A) = 0.5 \; \; P(B) = 0.25 \; \; P(C) = 0.125 \; \; P(D) = 0.125
$$
We could encode the transmission as:
A = 00
B = 01
C = 10
D = 11
But, since we have a given probability, we could use that to design an encoding that expoit this knowledge in order to reduce the size of the transmission:
A = 0
B = 10
C = 110
D = 111
This encoding uses on avarage 1.75 bits per transmission instead of 2.
More in general, with a given source X of V possible values with a probability distribuition the best coding allows a transmission with an avarage number of bits of
$$
H(X) = - \sum_j p_j log_2(p_j)
$$
With H(X) entropy of X.

### Entropy
High entropy means that the probability are similar, and we would have a flat histogram.
On the other end, low entropy means that some symbols have a much higher probability than others and the istograms will have some peaks.

Splitting a dataset in two parts changes the entropy that becomes the weighted sum of the entropies of the two parts:
$$
H(c| d: t) = H(c| d < t) * P(d < t) + H(c| d \geq t) * P(d \geq t) 
$$
with c the class attribute, t a threshold value on wich we split the dataset and d a real-valued attribute.
We can now define $IG(c|d : t) = H(c) - H(c|d :t)$ the information gained with the split
and $IG(c|d) = \max_t IG(c| d : t)$ the maximum possible information gained with a splitting

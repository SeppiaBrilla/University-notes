It is primarily used in telecommunications, and it is based on the concept of _[[Entropy]]_.

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
But, since we have a given probability, we could use that to design an encoding that exploit this knowledge in order to reduce the size of the transmission:
A = 0
B = 10
C = 110
D = 111
This encoding uses on average 1.75 bits per transmission instead of 2.
More in general, with a given source X of V possible values with a probability distribution the best coding allows a transmission with an average number of bits of
$$
H(X) = - \sum_j p_j log_2(p_j)
$$
With H(X) entropy of X.

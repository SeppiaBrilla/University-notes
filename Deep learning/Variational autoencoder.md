An autoencoder is a net trained to reconstruct input data out of a learned internal representation
![[Pasted image 20230519214219.png]]

But, if we force the latent space to have a fixed, predetermined distribution, we can use this knowledge to explore the latent space.
![[Pasted image 20230519214421.png]]

## Conditional VAE

We would like our nets to generate any type of data, and not only a songle one. To do so, we can make the network learn a different distribution depending on the given data. We can force this by adding a label to the input.
![[Pasted image 20230520125309.png]]
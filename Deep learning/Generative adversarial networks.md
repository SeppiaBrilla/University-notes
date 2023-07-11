We can model two networks: one that tries to generate new data and another one that tries to discriminate between real and fake data.
![[Pasted image 20230519214907.png]]

The complete training process is:
```python
def train():
	for _ in range(train_steps):
		for _ in range(discriminator_steps):
			noise = sample_noise_from_prior(m)
			example = sample_example_from_generating(m)
			update_discriminator(noise, example)
		noise = sample_noise_from_prior(m)
		update_generator()
```

The discriminator is trained with the formula:
$$
\nabla_{\theta_\sigma}\frac{1}{m}\sum_{i = 1}^m \left[\log D(x_i) + \log (1 - D(G(z_i)))\right]
$$
While the generatori is trained with the formula:
$$
\nabla_{\theta_\sigma}\frac{1}{m}\sum_{i = 1}^m \log(1 - D(G(z_i)))
$$


## Conditional Gans

If, as in the case for [[Variational autoencoder|CVAEs]] we want the generator to generate different data depending on a imput label, we must also modify the discrimiator so that it can classify not only real or fake data but also what the data is representing.

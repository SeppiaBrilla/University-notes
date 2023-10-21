produce $\alpha$ with an iterative procedure:
```python
# f is the function, x is the current value of x_k, p is the direction
def armijo(f, x, p):
	a = 1
	u = 1/4
	while f(x) - f(x + a * p) <= u * a * np.norm(f(x))**2:
		a = a / 2
	return a
```
the procedure always converges and choosing alpha with this method guarantee also the convergence of the [[Gradient method]].
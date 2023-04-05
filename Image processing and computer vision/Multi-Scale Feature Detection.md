
In order to achieve the scale invariance property that the [[Corner detection|Harry's corner detection]] lack, we can fix the scale of an image and apply a [[Gaussian filter]] to smooth the image => $L(x,y,\sigma) = G(x,y,\sigma)*I(x,y)$. 
If we apply this to the [[Edge detection|LOG]] operation we obtain:
$$
F(x,y,\sigma) = \sigma^2\nabla^2L(x,y,\sigma) = \sigma^2(\nabla^2G(x,y,\sigma)*I(x,y)
$$
where the $\sigma^2$ factor is a normalization factor that avoid the weakener of the derivatives with high sigma values.
Then, if we check the extrem values, we can get some feature and thus, get a good detector to use in [[Local invariant feature]].
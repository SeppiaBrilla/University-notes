In the [[Perspective projection]] we assume, as a model, the pinhole camera. However, that model has a major flaw: the amount of light captured is very low. In order to solve the problem, we have two possible solutions:

- Encrease the hole (this results also in a blurrier image because each point in the original image is now a cone in the new image)
- Take more light over time (this could lead to a motion blur problem if the image has object in moovements)

In order to ease the problems of the first solution, we can use Lenses.
The pinhole model assume an infinite deptho of view, lenses limit that depth to a certain amount but allow a bigger hole and, as a consequence, more light.
![[Pasted image 20230227161920.png]]

- P is the scene point
- p is the focussed image point
- u is the distance from P to the lens
- v the distance from p to the lens
- f is the focal length (parameter of the lens)
- C center of lens
- F focal point of the lens

Choosing the distance of the image plane determines the distance at which scene points appear on focus image
$$
\frac{1}{u} + \frac{1}{v} = \frac{1}{f} \rightarrow u = \frac{vf}{v - f}
$$
But to acquire scene points at a certain distance we must set the position of the image plane accordingly
$$
\frac{1}{u} + \frac{1}{v} = \frac{1}{f} \rightarrow v = \frac{uf}{u - f}
$$

Given a choosen point, every other object in a different focus point will appear out of focus.
Those other points will be called __circle of confusion or blurr circle__.

## Diaphragm

It is the mechanical part that control the amount of light gathered by the camera.

## Focusing mechanism

![[Pasted image 20230302182143.png]]

With a focal length long as the distance from p to the lens, we obtain a focus point at infinity, in any other case, the focus point move and the point in focus change.
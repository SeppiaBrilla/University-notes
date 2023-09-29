Several Computer Vision tasks deal with finding “Corresponding Points” between two (or more) images of a scene ([[Stereo vision]]). This can be difficult for several reasons (e.g. viewpoint variations, different lighting conditions...).

The task of finding correspondences in two images can be split in 3 steps:
1) __Detection__ of salient points
2) __Description__: computation of a suitable descriptor based on pixels in the keypoint neighborhood (use a single pixel can lead to multiple error because it is easy to mistake it, since the same intensity may be easy to find in multiple locations)
3) __Matching__ descriptors between images.
__Descriptors should be invariant (robust) to as many transformations as possible__

### Properties of good detectors 
- __Repetability__: it should find the same keypoints despite the possible transformation of the image.
- __Saliency__: it should find keypoints surrounded by informative patterns

### Properties of good descriptors
- __Distinctiveness vs. Robustness Trade-off__: the description algorithm should capture important information around the chosen keypoint so to keep salient token and ignore changes due to noise or change in the scene
- __Compactness__: the description should be as small as possible to minimize memory occupancy and computational cost.

### Detectors
- [[Moravec detector]]
- [[Multi-Scale Feature Detection]]
- [[Difference of gaussian (DOG)]]

### Descriptors
Once the keypoints have been found, we need to find a descriptor for each keypoint. We would like a descriptor to have these properties:
- Scale invariance => the patch is taken from the stack of images (𝐿(𝑥, 𝑦, 𝜎) in Lowe’s) that correspond to the characteristic scale
- Rotation invariance => a [[canonical orientation|canonical]] (aka characteristic) patch orientation is computed, so that the descriptor can then be computed on a canonically-oriented patch

An example of a descriptor is: [[SIFT descriptor]]

## Matching process

Descriptors are compared across diverse views of a scene to find corresponding keypoints with a [[K nearest classifier|K nearest]] matching algorithm.
The matching process search, for each feature in the target image, the closest reference point in the reference image. When matching [[SIFT descriptor|SIFT]] descriptors, the distance typically used is the Euclidean distance.
The found NN does not necessarily provide a valid correspondence, as some features in the target image may not have a corresponding feature in the reference image.
To fix this problem, we could threshold the match: $\frac{d_{NN}}{d_{2_NN}}\leq T$. The second criteria is always less than 1 and. Lowe shows that T=0.8 may allow for rejecting 90% of wrong matches while missing only 5% of those correct
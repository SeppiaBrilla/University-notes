The SIFT (Scale Invariant Feature Transform) descriptor is computed as follows:  
1) A 16x16 oriented pixel grid around each keypoint is considered
2) This is further divided into 4x4 regions (each of size 4x4 pixels)
3) A gradient orientation histogram is created for each region
4) Each histogram has 8 bins (i.e. bin size 45°)
5) Each pixel in the region contributes to its designated bin according to:
	1) Gradient magnitude  
	2) Gaussian weighting function centred at the keypoint (with σ equal to half the grid size)
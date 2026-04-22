Portable Network Graphics, entirely lossless

**Filtering (prediction)**
Delta encoding, where each value is a difference from the previous value.
[2,3,4,5,6,7,8] becomes [2,1,1,1,1,1,1]

PNG does this relating to the pixel to the left above and above left

![[Pasted image 20260422115129.png]]The filter takes ABC and predicts X. There are 5 PNG modes to be chosen.
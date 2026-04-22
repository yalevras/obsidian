Portable Network Graphics, entirely lossless

**Filtering (prediction)**
Delta encoding, where each value is a difference from the previous value.
[2,3,4,5,6,7,8] becomes [2,1,1,1,1,1,1]

PNG does this relating to the pixel to the left above and above left

![[Pasted image 20260422115129.png]]The filter takes ABC and predicts X. There are 5 PNG modes to be chosen.
- No filtering
- Difference between X and A
- Difference between X and B
- Difference between X and (A+B)/2
- Paeth predictor (linear function of A,B,C) https://www.w3.org/TR/PNG-Filters.html
![[Pasted image 20260422115659.png]]
These filters are done per channel, such as all the red values of a pixel for a scanline. Every row will use the same filter though and this can change.

To choose the best filter, brute force is too much, so some rules of thumb were established. For palette images and sub-8 bit grayscale images, None filters are best. For other images, choosing the filter that minimizes the sum of absolute differences. Choose the filter that gives the smallest sum.

**Compression (DEFLATE)**
The results of filtering then goes through an algorithm called DEFLATE combining LZ77 coding along side Huffman encoding
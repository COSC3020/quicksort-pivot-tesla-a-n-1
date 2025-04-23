# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

## Background from the slides

According to slide 34:

  - On average, our choosen pivot is equally likely to be the ith smallest for any i = 1, 2, ..., n
  - With probability 1/2, the pivot will be from the middle n/2 elements (considered good pivots)
  - A good pivot creates two partitions of size at most 3n/4
  - We expect to pick one good pivot every two tries

## Median of Three Analysis

When using the median of 3 method, we select the first, middle, and last elements of the array and choose the median value as the pivot.

### Categorizing elements in 3 groups:

  - S: Elements smaller than good pivots (bottom n/4)
  - G: Good pivot elements (middle n/2)
  - M: Elements larger than good pivots (top n/4)

### Based on description in slide:

  - P(S) = 1/4 (probability of an element being smaller than good pivots)
  - P(G) = 1/2 (probability of an element being a good pivot)
  - P(M) = 1/4 (probability of an element being larger than good pivots)

## Possible Combinations and Calculating Probabilities

For this method, we need to analyze all possible combinations of S, G, and M for the three selected elements.

### Enumerating all possible combinations:

  1. All elements of the same type:
  
    - P(SSS) = (1/4)^3 = 1/64

    - P(GGG) = (1/2)^3 = 1/8 = 8/64  Good Pivot
    
    - P(MMM) = (1/4)^3 = 1/64
    
  2. Two elements of one type, one of another (3 positions for the different element):
  
    - P(SSG) = 3 x (1/4)^2 x (1/2) = 3/32 = 6/64
    
    - P(SSM) = 3 x (1/4)^2 x (1/4) = 3/64
    
    - P(SGG) = 3 x (1/4) x (1/2)^2 = 3/16 = 12/64  Good Pivot
    
    - P(SMM) = 3 x (1/4)^2 x (1/4) = 3/64 
    
    - P(GGM) = 3 x (1/2)^2 x (1/4) = 3/16 = 12/64  Good Pivot
    
    - P(GMM) = 3 x (1/2) x (1/4)^2 = 3/32 = 6/64
    
  3. One element of each type (6 different arangements):
  
    - P(SGM) = 6 x( (1/4) x (1/2) x (1/4) ) = 6 x 1/32 = 6 x 2/64 = 12/64  Good Pivot

### Good Pivot Combinations

Good pivots: (12/64) + (12/64) + (12/64) + (8/64) = 44/64 = 11/16 = 68.75% 

## What this means

With the first element selection method, the probability of choosing a good pivot is 1/2 or 50% because any element has a 1/2 chance of being in the middle n/2 elements. The median of three method increases the probability from 50% to 68.75%, which is a great improvement. 

On average, using quicksort with the median of three method will create better balanced partitions and better performance.

Sources: [GeeksforGeeks](https://www.geeksforgeeks.org/quicksort-using-median-of-medians-algorithm/) [This quicksort method visualizer](https://visualgo.net/en/sorting)

"I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice."



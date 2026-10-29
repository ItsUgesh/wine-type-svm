## 1. Which kernel performed best?
The Linear kernel performed best, with an accuracy of 99.77% (3 wrong out of
1,300 test wines). RBF was almost identical at 99.69% (4 wrong), and Polynomial
was slightly lower at 99.46% (7 wrong). The gap between Linear and RBF is a
single wine, so the two kernels are effectively tied; only the Polynomial kernel
is clearly behind (0.31 percentage points, about 4 more wines).

## 2. Why might one kernel be better than the others?
- **Linear** separates the classes with a flat boundary. It performing as well as
  the more flexible kernels shows that red and white wines are almost linearly
  separable: a straight plane in the standardized feature space is enough.
- **RBF** can curve the boundary around groups of points, but here there was
  almost nothing left to gain from the extra flexibility.
- **Polynomial** draws a curved boundary with a fixed shape. It was the least
  accurate, probably because its curve is less well matched to this data and it
  is more sensitive to its settings.
- Red and white wines differ strongly in their chemistry (for example, white
  wines usually have much more sulfur dioxide), so all three kernels score above
  99%. For comparison, always guessing "white" would give about 75%.

## 3. What happens when C changes to 0.5 or 5?
C controls how strictly the model punishes mistakes on the training data.
- **Linear:** no change (99.77% for every C, 3 wrong). The data is so cleanly
  separated that C does not matter.
- **RBF:** a tiny gain from C = 0.5 to C = 1 (99.62% to 99.69%, one wine), then
  no further change.
- **Polynomial:** the clearest effect. Accuracy rises with C (99.15%, 99.46%,
  99.54%; 11, 7 and 6 wrong wines). A small C makes the polynomial boundary too
  smooth and it underfits, while a larger C lets it fit the training data more
  closely.
Overall the models are not very sensitive to C, except the polynomial kernel.

## Conclusion
The Linear kernel is the best choice: it has the highest accuracy (99.77%) for
every C, it is the simplest and fastest model, and it does not need tuning. RBF
is a close second. Because the test set has only 1,300 wines, differences of one
or two wines (about 0.1 points) are within noise and should not be over-interpreted.

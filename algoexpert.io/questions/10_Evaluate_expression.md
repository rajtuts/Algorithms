### 10. Evaluate Expression Tree ⚪⭐

You're given a binary expression tree. Write a function to evaluate this tree mathematically and return a single resulting integer.

All leaf nodes in the tree represent operands, which will always be positive integers. All of the other nodes represent operators. There are 4 operators supported, each of which is represented by a negative integer:

* -1 : Addition operator, adding the left and right subtrees.

* -2 : Subtraction operator, subtracting the right subtree from the left subtree.

* -3 : Division operator, dividing the left subtree by the right subtree. If the result is a decimal, it should be rounded towards zero.

* -4 : Multiplication operator, multiplying the left and right subtrees.

You can assume the tree will always be a valid expression tree. Each operator also works as a grouping symbol, meaning the bottom of the tree is always evaluated first, regardless of the operator.

Sample Input
```
tree= -1
     / \
   -2  -3
  / \ / \
 -4 2 8 3
 / \
2  3
``
Sample Output
6 // (((2 * 3) - 2) + (8 / 3))

Hints

Hint 1

This problem will be easiest to solve using recursion. Can you think of what the recursive subproblems would be? And what is the base case?

Hint 2

For each operator, a recursive call can be made on its left and right values. The result of these recursive calls can then be combined using that operator. The base case to finish recursing will be when we reach an operand, which is any positive integer.

Optimal Space & Time Complexity

O(n) time | O(h) space - where n is the number of nodes in the Binary Tree, and h is the height of the Binary Tree

```
import java.util.*;

class Program {
    // This is an input class. Do not edit.
    static class BinaryTree {
        public int value;
        public BinaryTree left = null;
        public BinaryTree right = null;

        public BinaryTree(int value) {
            this.value = value;
        }
    }

    // O(n) time | O(h) space - where n is the number of nodes in the Binary Tree,
    // and h is the height of the Binary Tree
    public int evaluateExpressionTree(BinaryTree tree) {
        if (tree.value >= 0) {
            return tree.value;
        }

        int leftValue = evaluateExpressionTree(tree.left);
        int rightValue = evaluateExpressionTree(tree.right);

        if (tree.value == -1) {
            return leftValue + rightValue;
        } else if (tree.value == -2) {
            return leftValue - rightValue;
        } else if (tree.value == -3) {
            return leftValue / rightValue;
        }
        return leftValue * rightValue;
    }
}
```

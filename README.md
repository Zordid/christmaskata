# It's Christmas Time

## Part 1 - Once upon a time there was a tree...
It's Christmas time and everybody needs a Christmas tree, right? We have a customer who needs many, many trees for the upcoming festivity!

### 1.1
Write a function that „draws“ a Christmas tree with ASCII characters (ASCII art). The „picture“should be returned as a *collection of strings*. See the following example of a tree with height 5:

e.g. ```drawTree(5)``` renders:    
``` 
     X
    XXX 
   XXXXX
  XXXXXXX
     X
```

As you can see, the tree has a centered trunk underneath its body and the height measured includes the trunk as well as the body of the tree.
Make sure you cover edge cases and think about implicit requirements of a tree's dimensions. In case of wrong input, no tree should be drawn and an empty picture must be returned.

### 1.2
Trees and strings, huh? Our customer needs a more flexible API. The returned structure should now be a *two dimensional array of characters*. Rework your API so that:

e.g. ```drawTree(4)``` now returns an array containing 4 arrays containing 5 characters each:
```
[
    [' ', ' ', 'X', ' ', ' '], 
    [' ', 'X', 'X', 'X', ' '], 
    ['X', 'X', 'X', 'X', 'X'], 
    [' ', ' ', 'X', ' ', ' ']
]
```

### 1.3
Wow, you can create two-dimensional-character-trees now. Can you guess why we did this?

Assume your ```drawTree``` function now accepts a two-dimensional array of characters and draws the tree into it! This would not be much fun without another nifty API cahnge: a tree can now be *placed* anywhere within the bounds of a canvas. To make things easy, the *tip of the tree* marks the tree's position.
The canvas' origin is (0,0) at the upper left corner.

To draw a tree now, we need:
* a canvas
* a tree height
* a tree origin

> Hint: the API does not necessarly need to be ```drawTree(canvas, height, x, y)``` - you are always free to find a better API! 

This means, given a canvas of 10 times 10 characters, a ```drawTree(canvas, height=5, x=3, y=2)``` would result in:
```
[
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', 'X', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', 'X', 'X', 'X', ' ', ' ', ' ', ' ', ' '],
    [' ', 'X', 'X', 'X', 'X', 'X', ' ', ' ', ' ', ' '],
    ['X', 'X', 'X', 'X', 'X', 'X', 'X', ' ', ' ', ' '],
    [' ', ' ', ' ', 'X', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
]
```

Try to think about "edge" cases and cope with them! Decide what would the customer want? (Hint: he requires perfectly shaped trees!)

### 1.4
It's time to grow a forest! Now that we can grow trees anywhere, why don't we make sure we can draw at least two trees on the same canvas.

Given a 10 times 10 character canvas, make sure multiple draw commands can be stacked upon another!

```drawTree(canvas, height=5, x=3, y=2)``` followed by ```drawTree(canvas, height=3, x=7, y=7)``` should result in:

```
[
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', 'X', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', 'X', 'X', 'X', ' ', ' ', ' ', ' ', ' '],
    [' ', 'X', 'X', 'X', 'X', 'X', ' ', ' ', ' ', ' '],
    ['X', 'X', 'X', 'X', 'X', 'X', 'X', ' ', ' ', ' '],
    [' ', ' ', ' ', 'X', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', 'X', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', 'X', 'X', 'X', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', 'X', ' ', ' ']
]
```

To prove your wood nursery capabilities - and to have some fun - show your skills by planting 10 trees at random positions on a larger canvase and celebrate your achievement with a Christmas cookie!

## Part 2 - Fight the competitors
Our customer gets trees from all around the world. Because he does trust us and our tests to deliver only perfectly shaped trees, he needs us to make sure all trees can be verified by him a second time.

### 2.1
Develop a function that takes a *collection of strings* and returns true only if a tree according to the defined standards above is visible.

e.g. this tree should be tested positive (true) by ```verifyTree(<collection of strings>): boolean```:
```
    X
   XXX
  XXXXX
    X
```
while this one...
```
    X
   XX
  XXXXX
    X
```
shouldn't, because its shape is not okay.
Try to cover all possible anomalies.

Now that we are able to grow trees anywhere we like, we must be able to find them again! Our customer doesn't want to lose sight of the trees for the wood, right?

### 2.2
Given our API is based on two-dimensional character arrays, we should update the API accordingly. The ```verifyTree``` function must accept a two-dimensional character array as well to verify the shape of trees.

### 2.3
The simple ```verfiyTree``` function does not yet know anything about origins of trees, it needs to be upgraded to support a supplied origin and a tested tree height.

This would result in a possibility to ask something like "is there a tree at origin (x,y) with the height h".
e.g. ```verifyTree(canvas, x, y, height): boolean```.  Think about what edge cases to detect. Are there implicit rules to be obeyed in order to savely detect a tree next to another tree? Does your function handle trees close to each other, but not touching, correctly? 

## Part 3 - You grow them, you find them... 

Almost there. With the tools you got now, it should be possible to detect all of the trees in a given canvas correctly. What is needed to scan the complete area for trees?
Write a function that takes a canvas and reports back all of the contained trees' origins!
```scanForTrees(canvas): list of origins```

## Part 4 - It's Christmas Day!
You are finally done. But we cannot celebrate Christmas unless we decorate our trees!
Each tree must carry a star on its tip, everybody knows that.

Use the input you got from your ```scanForTrees``` function to decorate all the trees you got with a star on top!
e.g.:
```
    X
   XXX
  XXXXX
    X
```
becomes
```
    *
    X
   XXX
  XXXXX
    X
```

Try to take the example input forest1.txt and forest2.txt from the GitHub repo to test your decoration skills!

# Merry Christmas!




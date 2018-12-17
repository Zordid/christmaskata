# It's Christmas Time

## Part 1 - Once upon a time there was a tree...

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

Assume your ```drawTree``` function now accepts a two-dimensional array of characters and draws the tree into it! This would not be much fun without another nifty API feature: a tree can now be *placed* anywhere within the bounds of a canvas. To make things easy, the *tip of the tree* marks the tree's position.
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

Try to think about "edge" cases and cope with them! Decide what would the customer want?

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

## Part 2 - You grow them, you find them...

### 2.1
Now that we are able to grow trees anywhere we like, we must be able to find them again!


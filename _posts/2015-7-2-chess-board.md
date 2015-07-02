---
layout: post
title: What we did today and the Chessboard Activity on Eloquent Javascript
---


![](https://googledrive.com/host/0BzxRUlDjwAFeUnREY1ZscXg0Q3c)

Today, it was very cold and rainy in Melbourne.  Sarah ate a salad for lunch and I went to Coles to get a Pepper Steak Pie with the 
squeeze tomato sauce - which despite my best efforts, didn't squeeze out.  What else... Sarah and I adjusted our seats to make it more ergonomically friendly.  Now that the
big events have been cover above, here are the other things we did:

* Attended 9am meeting @ Redbubble
* Caught up on our social media feed and did some outreach
* Edited css in our blog
* Did the group photo
* Photoshopped the group photo with more photoshopping to come for our coaches that couldn't be there (can you tell the below photo was photoshopped?)
* Going through the ember.js docs
* Going through exercises on eloquent javascript (the chessboard activity has a subheading of its own - check it out below) - which is a fantastically written book.

![](https://googledrive.com/host/0BzxRUlDjwAFeMksyUFg0Uk1HZ0E)

### The Chessboard Activity on Eloquent Javascript

Both Sarah and I went through the codecademy Javascript course while on holidays last month.  I think the codecademy provides you with the
basics, but the book 'Eloquent Javascript' is fantastic.  In chapter 2, there are three activities.  The last of those activities is 
to create a chessboard pattern like this: # # #, then on the next line,  # # #, with the space and the hashes alternating.

This was my (butchered) code and Sarah helped me get it working with commentary... 

```
var size = 8;
var start = "# ";
var board = ""
var count = 0;

for (y = 0; y < size; y++) {
    // starting piece
    if (count % 2 == 0) { // even
      board += start[0];
    }
    else { // odd
      board += start[1];
    }
  for (i = 0; i < size - 1; i++) {
    // the other 7 pieces
    var lastPiece = board[board.length - 1];
    if (lastPiece === " ") {
      board += "#";
    } else if (lastPiece === "#") {
      board += " ";
    } else {
      board += board[board.length -3];
    }
  }
  board += "\n";
  count++
}
console.log(board)
```

Let's talk about this... as I looked at the pattern, I could see it was a string that went through a pattern # # # and then had the 
newline character "\n" which then forms part of the string.  The loop I had considered the last piece, so that if that last piece in the
pattern was a #, then it would do a " " (space) next.  The problem came, as the last piece could also be a "n" from the newline character,
if that occurred, the 'else' statement would take care of it and then jump back to the character before the "\n" - hence the board.legnth - 3.
Also the variable lastPiece needed to be a local variable that would change based on the loop.

So that was the pattern, however, I had the problem of the pattern adding an additional character in the first line when var board = "#" at the 
start.  Sarah added in this code:

```
for (y = 0; y < size; y++) {
    // starting piece
    if (count % 2 == 0) { // even
      board += start[0];
    }
    else { // odd
      board += start[1];
    }
```

which meant that for the first column, the first item, if an even number, would display # and if an odd number, would display a space.
This also gave us the starting point for our pattern in the secondary loop.  The secondary loop would loop size - 1 = (8 - 1) = 7 times because
we already had our starting point for each row.

Now it was done.... yay!  But this was really cumbersome compared to the solution.

The solution was very elegant and eloquent.  It was:

```
var size = 8;

var board = "";

for (var y = 0; y < size; y++) {
  for (var x = 0; x < size; x++) {
    if ((x + y) % 2 == 0)
      board += " ";
    else
      board += "#";
  }
  board += "\n";
}

console.log(board);
```

Instead of seeing the pattern as a string, it saw the board as a mathematical grid with an x & y - remember the cartesian plane from 
high school?
So it x = 1 and y = 1 then that location would be (1,1) and when you add 1 and 1 you get 2 which is divisible without remainder by 2.
Therefore, it would be a space.  
It makes sense.  The first item was a # and the 2nd item was a space.
At the same x point (1) and the second row (y = 2) you'd get 3.  Three is not divisible evenly by 2, so that board would put a #.

" "
#

going down a column.  The pattern would also go well horizontally too.
Such a great solution!


### Other stuff worth commenting about today:

* The airconditioner went on and it sounded like a rocket.
* It's harder to photoshop in open eyes in a photo that it looks.  

Signing off...




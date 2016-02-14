---
title: Explaining Our String Segmentation Code
---

The code that my group came up with contains three different constantly moving parts. A counter variable (counter), a right-to-left moving index variable and an increasing and intermittently re-setting "cut" variable that works in tandem with the index. That comes later on in the code, though. It begins with a simple test of "is this string a valid word itself?" basically, and if so, add that to the array of words:

  <pre><code>if valid_word?(str)
    arr << str</code></pre>

If the string is not a word in itself, it moves on to the next bit:

  <pre><code>else
    while counter < str.length
      test_word = str[index, cut]</code></pre>

This is saying that while the counter number is less than the total value of the string (just starting off a count for this loop...), the the test_word argument for the upcoming loop will build up strings by starting at the right (index = -1) and taking those characters one at a time (cut = 1). This was the hardest part for me to understand. I get it now, but it still doesn't seem intuitive to me to just say str[this, that] and expect that to do something for me. It's like... too simple? And each re-appearance of "str" kind of stops me up and I have to think really hard about the difference between that and test_word.

On the next bit of code, if the character that was cut from the end of the string is a valid_word, that test_word gets pushed into the array and the index goes back to -1, cut keeps chomping off characters one at a time, the counter variable still keeps counting by 1. 

      if valid_word?(test_word)
        arr << test_word
        index -= 1
        cut = 1
        counter += 1

If the character that got cut from the end of the string is not a valid_word, then the index keeps moving backwards through the string from right to left, the amount of characters that get cut and checked for validity is going to increase by 1 more, and the counter keeps going up, keeping track of where we're at in the length of the string.

      else valid_word?(test_word) == false
        index -= 1
        cut += 1
        counter += 1

Since the string is being deconstructed right to left, the words pushed into the array are going to be in reverse order of how they appear in the string, so we've got to flip those around:

  <pre><code>arr.reverse</code></pre>

This code passes our tests and takes care of the issue of cutting words off prematurely without their suffixes (like "basement" -- instead of cutting off "base" and being left over with "ment" which is not a word). But we're still left with the problem of prefixes. We just traded one problem for another, essentially, and we're going to have to come up with a solution for that in order for this to function properly with <i>any</i> string it might encounter. 
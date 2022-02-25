# Code review comparison

[My repository](https://github.com/w2llS/markdown-parse)

[Reviewed repository](https://github.com/w2llS/markdownParse-reviewed)



This is how I made the tests

![Image](/report4Images/1.PNG)


---
Snippet 1 should produce
```
`google.com
google.com
ucsd.edu
```

For my implementation the test failed

![Image](/report4Images/2.PNG)

For the reviewed implementation the test passed



---
Snippet 2 should produce
```
a.com
a.com(())
example.com
```

For my implementation the test failed

![Image](/report4Images/3.PNG)

For the reviewed implementation the test failed

![Image](/report4Images/4.PNG)


---
Snippet 3 should produce
```
https://www.twitter.com
https://ucsd-cse15l-w22.github.io/
https://cse.ucsd.edu/
```

For my implementation the test failed

![Image](/report4Images/5.PNG)

For the reviewed implementation the test failed

![Image](/report4Images/6.PNG)

I think that I can make a change in my code that would make it work for snippet 1. I could do this by making my code ignore parenthesis that are in between 2 backticks. I would need new variables and some lines to keep track of the backtick indexes but it should not take more than 10 lines of code.

I do not think 10 lines would be enough to fix my code to work for snippet 2, as I would need a check for nested links, nested brackets and nested parenthesis, which would need a lot more variables and lines of code to keep track of.

I think 10 lines is not enough for snippet 3 as I would need to add some checks for when there are spaces before the link and remove those spaces/only return the link without spaces. Then I would need to add a check to ensure there is a close parenthesis after an open one before returning it, as right now my code returns the whole paragraph of text.

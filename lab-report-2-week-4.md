# Code change 1

The first error that I encountered was from [test-file2](https://github.com/w2llS/markdown-parse/blob/new/test-file2.md)

### Symptom

Command
```
PS C:\UnityProjects\Github\markdown-parse>  java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore MarkdownParseTest
```
Output

```
1) testFile1(MarkdownParseTest)
java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOfRange(Arrays.java:3822)
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParseTest.testFile1(MarkdownParseTest.java:19)
```
This is the change I made

![Image](/report2Images/1.PNG)

Write 2-3 sentences describing the relationship between the bug, the symptom, and the failure-inducing input.

The bug is that there is an IOException when trying to get the links of the input test-file2.md. This is because in test-file2 there is text after the links. Which cause the method to go in an infinite while loop as there is no more "[" character after current index. So we added a check for "[" after the currentindex of the current characters in the markdown file and stop the while loop there if there are no more.



# Code change 2

The second error that I encountered was from [test-file3](https://github.com/w2llS/markdown-parse/blob/new/test-file3.md)

### Symptom

Command
```
PS C:\UnityProjects\Github\markdown-parse>  java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore MarkdownParseTest
```
Output


```
There was 1 failure:
1) testFile1(MarkdownParseTest)
java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 27
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)
        at java.base/java.lang.String.substring(String.java:2704)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParseTest.testFile1(MarkdownParseTest.java:19)
```
This is the change I made

![Image](/report2Images/2.PNG)

The bug is that there is a StringIndexOutOfBoundsException when trying to get the links of the input test-file3.md. This is because in test-file3 there is a "[]" but there is no paranthesis. Thus the indexOf method returns -1 and when returning the link the method tries to get a substring of index 0 to -1, which would return that error. So we added a check for square brackets and parenthesis and breaks the while loop if any of the integers return -1.



# Code change 3

The third error that I encountered was from [test-file5](https://github.com/w2llS/markdown-parse/blob/new/test-file5.md)

### Symptom

Command
```
PS C:\UnityProjects\Github\markdown-parse>  java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore MarkdownParseTest
```
Output


```
There was 1 failure:
1) testFile1(MarkdownParseTest)
java.lang.AssertionError: expected:<[page.com]> but was:<[]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testFile1(MarkdownParseTest.java:20)
```
This is the change I made

![Image](/report2Images/3.PNG)

The bug is that the test fails as the method would see the text in the parantheses as a link even if it was not beside the brackets. Thus to fix it we added a check to see if the openParen index was right after the close square bracket index. Thus it would make sure the link was actually a link and not seperated.

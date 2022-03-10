# MarkdownParse comparison

The two .md files that I want to compare is 194.md and 201.md

I used diff find all the differences between my results.txt and Joe's markdownparse results.txt

---

## test file 194.md

My results

```
[]
```

Joe's results

```
[url]
```

I believe that both our implementations were incorrect as I believe the right output should have been
```
my_(url)
```

To make my code be able to get this expected output I think I should modify my checks for close brackets as currently in my code it only finds links with proper format and if open parenthesis is 1 character after close bracket "](". I could add some checks to see if there were colons after the close bracket


## test file 201.md

My results

```
[]
```

Joe's results

```
[baz]
```

I believe that my implementation was correct as there should have been no links returned, the markdown previewww shows no links
```
[]
```

I think Joe's code returned baz because it checks for the next open parenthesis after the close bracket. However there was a < bar > in betweeen and this probably caused the formatting to be wrong and thus not show any links on the preview. So I ithink that the code can be fixed by checking for < > in between the link text and the URL. If it does find that then probably cancel the loop and not add the link to the return
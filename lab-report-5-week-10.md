![last umi](lab5ss/momentring.jpg)

# Lab Report 5 (LAST ONE ALREADY!!!)

## Difference 1

![diff1](lab5ss/diff1.png)

There was a difference between the results from test file 32.md. The text in the file is as follows

```
[foo](/f&ouml;&ouml; "f&ouml;&ouml;")
```

and the VSCode preview produces a link that leads to `föö` as the output. This means that it's a bug in both programs. This has to do with the translation from the markdown format to the html format, since those ö characters aren't typically used so it has a translation for the `&ouml;` series of character to the &ouml; character. Joe's Markdown Parse implementation also eliminates all links that contain a space, resulting in no link being printed. For mine code, it just doesn't do the translation since there was no elimination for the any space characters. This format for a link seems to a special case that isn't accounted for based on the html translation of characters. Through a bit more testing using 

[this](hello "link thing")

which has 

```
[this](hello "link thing")
```
Hovering over the link preview the contents of the quotations while the actual link is the part not in quotations, as seen by the following

![preview](lab5ss/firstTest.png) ![link](lab5ss/firstTestP2.png)

That would mean that the link pulled would have to be that part not contained in the quotation. The way to fix this would be to pull out anything inside of quotations and find the link before the space between the link and the quotations.

The fix for this would be within the part to determines the eligibility of a line inside (the parenthesis). My code does not have this yet at all While Joe's does around line 75 but needs to be heavily modified with `if else` statements to give it 

## Difference 2

![diff2](lab5ss/diff2.png)

the file contains
```
[link](   /uri
  "title"  )

```

There is a bug in both codes again. It uses the same syntax as the previous failed test, meaning it has a space character inside it, but it also has a \n character as well. Joe's code actually elimates all uses of both of those characters while mine doesn't not even consider them. The way that the link is actually registered is that the case is eliminated if there are two back to back \n\n characters, meaning it's a fairly simple fix on Joe's code where you'd only need to change the
```
potentialLink.indexOf("\n") == -1
```
to
```
potentialLink.indexOf("\n\n") == -1
```
in line 75. 

After doing this, you just have to make sure to remove any \n character if it's alone. Doing this will fix it for Joe's code with the exception of different syntax mentioned in the previous section. For my code, simliar fixes to Joe's code should be made, once the implementation for sensing what's inside the parenthesis is implemented. 

## Difference 3

![diff3](lab5ss/diff3.png)

The actual file contains
```
[foo *[bar [baz](/uri)](/uri)*](/uri)
```

Both of these have a bug. I believe the `/` character is actually used to designate the the link as a child directory in the current webpage url so an implementation for that needs to be added. Clicking on these types of links would require knowing the current webpage url. It also has to do with nested urls. The way that the VSCode preview reads it is that it takes the inner most url and ignores all of the external, however I know from previous testing that it only accepts the external most url if it's a valid url. 

That means the actual url for this is `parentLink/uri` so Joe's and my code is missing the parent url while mine is missing anyway for the code to find nested urls. That's a planned fix for my code at the time while Joe's already has the nested urls but still needs the other part. 

## Why didn't I use `diff` to find the differences?

Well the answer is in the second difference that there was a link in my code that resulted in new lines being printed in the results.txt of my code. That meant that every line after that was incorrect causing diff to give non-sensical output of a whole ton of different outputs primarily due to the offset of the test file and the line. 

# Conclusion between the 3 bugs

So the first file was a bug in how it interprets the `link "preview text"` format inside the parenthesis. That's one fix that would need to be made as well as html conversion for special characters. The second bug for both codes had errors regarding new lines which is an easy fix for Joe's code and a harder fix for my code due to my lack of any `.contains()` section. The last section had a bug regarding nested brackets and link syntax that Joe's code handles while mine cannot without a significant addition to the code as well as a bug that has to do with parent directories for links. The parent directory I have no idea how it would be implemented if you wanted to get that type of link but it would probably need some sort of recursive search for the uppermost parent directory. 

# GOODBYEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEE


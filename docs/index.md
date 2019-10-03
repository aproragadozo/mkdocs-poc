<!--
[TOC]
-->

# Thank you for your interest in our POC {: #title-header .title level='one' }

Paragraphs are separated by a blank line.

2nd paragraph. *Italic*, **bold**, and `monospace`.

I wonder if collapsible sections work:

<details>
  <summary>Click to expand!</summary>
  <h2>Heading</h2>
  <ol>
    <li>A numbered</li>
    <li>list
        <ul>
            <li>With some</li>
            <li>Sub bullets</li>
        </ul>
    </li>
    </ol>
</details>

Itemized lists look like this:

* this one
* that one
* the other one

The content between the two horizontal lines below is transcluded from `alma.txt`.

1. An ordered list starts *before* the transclusion.

---

{! docs/alma.txt !}

---

1. The ordered list terminates *after* the transclusion.

```Bash tab=
#!/bin/bash
STR="Hello World!"
echo $STR
```

```C tab=
#include

int main(void) {
  printf("hello, world\n");
}
```

```C++ tab=
#include <iostream>

int main() {
  std::cout << "Hello, world!\n";
  return 0;
}
```

```C# tab=
using System;

class Program {
  static void Main(string[] args) {
    Console.WriteLine("Hello, world!");
  }
}
```

> Block quotes are
> written like so.
>
> They can span multiple paragraphs,
> if you like.

Use 3 dashes for an em-dash (---). Use 2 dashes for ranges (e.g. "It's all in chapters 12--14."). Three dots ... will be converted to an ellipsis.

Unicode is supported.☺

## An h2 header

Here's a numbered list:

1. first item
2. second item
3. third item

You can optionally mark the
delimited block for Pandoc to syntax highlight it:

```python
import time
# Quick, count to ten!
for i in range(10):
    # (but not *too* quick)
    time.sleep(0.5)
    print i
```

### An h3 header

Now a nested list:

1. First, get these ingredients:

      * carrots
      * celery
      * lentils

2. Boil some water.

3. Dump everything in the pot and follow
    this algorithm:

    1. find wooden spoon
    2. uncover pot
    3. stir
    4. cover pot
    5. balance wooden spoon precariously on pot handle
    6. wait 10 minutes
    7. goto first step (or shut off burner when done)

    !!! Note
        Everything not saved will be lost.

Notice again how text always lines up on 4-space indents (including
that last line which continues item 3 above).

Here's a link to [a website](http://example.com).

Tables can look like this:

|size|material|color|
|----|------------|------------|
|9|leather|brown|
|10|hemp canvas|natural|
|11|glass|transparent|

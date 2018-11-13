

---
## Few link to read on markdown:

[Markdown Navigation](https://docsify.now.sh/custom-navbar)

[Markdown Readme 1](http://aplib.github.io/markdown-site-template/docs/layout.html)

[Markdown Readme 2](https://commonmark.org/help/)

[Another Readme 3](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

[Another Readme 4](https://sourceforge.net/p/opensidebarx/wiki/markdown_syntax/)

[Another IMP readme on Markdown](https://www.markdownguide.org/getting-started/)

[Another link for read to doc](https://docs.readthedocs.io/en/latest/intro/getting-started-with-sphinx.html)

---
## Few readthedoc link:
https://amitmund-demo.readthedocs.io/en/latest/index.html

https://abcd-samvrita.readthedocs.io/en/latest/

https://amitmund.readthedocs.io/en/latest/

example to follow:
https://raw.githubusercontent.com/rtfd/readthedocs.org/master/docs/index.rst

I believe for read the doc, need to create work on rst file and not sure about md file yet.

https://mkdocs.readthedocs.io/en/0.9/user-guide/writing-your-docs/


---
## Few other tools and links:
https://remarkjs.com/#1\
http://jdan.github.io/cleaver/#1\
https://www.deckset.com/

---
## Documentation (This is IMP)
https://readthedocs.org/  -> One of the best thing to try for the documentation.



---
# heading1
## heading2
### heading3
#### heading4
##### heading5
###### heading6

---
*Italic*

**Bold**

***BoldItalic***

---
[Link](http://a.com)

![Image](http://url/a.png)

---
> Blockquote

---

* List
* List
* List

---
1. One
2. Two
3. Three

---

Horizontal Rule

---

`Inline code` with backticks

---

```
# code block
print '3 backticks or'
print 'indent 4 spaces'
```

---

[Learning1](https://commonmark.org/help/tutorial/)

[Learning2](https://commonmark.org/help/tutorial/02-emphasis.html)

---
to put * use the \* 

For a line break, add either a backslash \ or two blank spaces at the end of the line.

---

I have eaten\
the plums\
that were in\
the icebox

---
My favorite Miss Manners quotes:

> Allowing an unimportant mistake to pass without comment is a wonderful social grace.
>
> Ideological differences are no excuse for rudeness.

---

You can do anything at <https://html5zombo.com>

---

[Another study link on markdown](https://www.markdownguide.org/getting-started)

---
Creating a table:

| Tables   |      Are      |  Cool |
|----------|:-------------:|------:|
| col 1 is |  left-aligned | $1600 |
| col 2 is |    centered   |   $12 |
| col 3 is | right-aligned |    $1 |

---

## image
Here's our logo (hover to see the title text):

Inline-style: 
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style: 
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

---

## inline html
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

---

<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE
" target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

---

Or, in pure Markdown, but losing the image sizing and border:

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](http://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)

---
Some more information:

https://github.com/cjsheets/mkdocs-rtd-dropdown/blob/master/docs/user-guide/configuration.md

```yaml
site_name: Marshmallow Generator
```

**default**: `null`

```yaml
repo_url: https://github.com/example/repository/
```

**default**: `'GitHub'`, `'Bitbucket'` or `'GitLab'` if the `repo_url` matches
those domains, otherwise the hostname from the `repo_url`

```yaml
# Query string example
edit_uri: root/path/docs/
```

```yaml
nav:
    - 'Introduction': 'index.md'
    - 'User Guide': 'user-guide.md'
    - 'About': 'about.md'
```

Source file      | use_directory_urls: true  | use_directory_urls: false
---------------- | ------------------------- | -------------------------
index.md         | /                         | /index.html
api-guide.md     | /api-guide/               | /api-guide.html
about/license.md | /about/license/           | /about/license.html

---




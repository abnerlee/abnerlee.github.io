---
layout: post
title:  "Why Typora ?"
date:   2015-03-11 23:26:52
summary: "The reason why I write another markdown editor, even though there're already too many markdown editors in this world. "
category: typora
---

Days ago, I released a markdown editor (beta version) for Mac — [typora][]. What makes it different among countless markdown editors in this world is that: it basically doesn't provide syntax highlighting for markdown source nor a separated view/window for previewing, instead, **it combines syntax highlighting for markdown source and the live preview function** in a single window seamlessly, thus make it possible for users to read and write acticles with markdown at the same time and in one window only. In other words, it goes like this:

<p><video src="http://typora.io/img/beta.mov" type="video/h.264" autoplay="autoplay" muted="muted" preload="preload" loop="loop" ></video></p>

Although it is in its early beta phase, I, personally, am very excited about my work and am using it as my default markdown editing & previewing app. Yes, there are many other markdown editors for mac, but I am not fully satisfied with any of them. *So what's wrong with most markdown editors ?*

## Preview Window Goes the Wrong Way

> The overriding design goal for Markdown's formatting syntax is to make it as readable as possible. The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions[^markdown-principles].

The principle of markdown's syntax design is **readable**, in other words, it *should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions*. Markdown editor should help to achieve this goal, by using better syntax highlight design to reduce / eliminate noisy information (such as tags or formatting instructions) and therefore, make the content itself pretty to read, instead of providing a fancy preview window which indicates users to write in one place and read in another, since in latter pattern, the readability of markdown itself is underestimate.

There are more reasons for me to hate preview window:

#### Seperated views for source and preview means there are duplicate information on my screen.

Many editors, such as [Mou](http://25.io/mou/), split their window into source section and preview section. It might be acceptable if I was using iMac with a bigger screen, but on my macbook, I cannot accept that, only half of my screen displays useful information (for the other half just displays duplicated text content) text input is only allowed in a narrow textarea. It is even wrose when I want to use half of my litter screen to read documents and half of my screen to take notes via markdown — I will only have 1/4 area for writing with preview feature turned on. 

Then think about a note-taking app like Evernote. Many person wants it to support Markdown, but now it has 3 sections in this main window, thus if it supports markdown, it may end up with 4 sections in its main window since a preview section will be provided to user. Therefore, I don't really want a preview view/window on my macbook.

#### Preview window is distracting

When we chose a *text editor* just for writing, we want it to be **Distractions Free**. One benefits of markdown, as frequently quoted by many markdown editors, is that — *the users does not need to care about the typesetting but only the content itself*. For applications with a preview window, however, content inside the preview window keeps changing and rendering, which is very annoy to me. Also, when I concentrate on writing into the source view, since I don’t know what it would look like after publishing, I may wonder whether the output is correct, duo to the fact that different markdown editors has different *dialect* to parse/render markdown, I may take a look at the preview window to check outputs form time to time and unconsciously. Therefore, *I will concern the style and typesetting while I am supposed to fully focus on writing content*.

#### Behavior in source view and preview are not identical

Developers sometimes use different technologies for source and preview. For example, use [CodeMirror](http://codemirror.net) or [Ace Editor](http://ace.c9.io) to highlight code fences in markdown source while using [Highlight.js](https://highlightjs.org) for exactly same purpose in preview window or exported HTML, but since they are different code, the code fences may be parsed and highlight in different ways between source window and preview window.

The worse thing is that: the markdown parser used for source highlight and preview is different. Open <https://stackedit.io/editor> for example, and input `a_b_c` in this source section. We can see “b” in source section is wrapped by `<em/>` while in preview section, it is not. Or input 

``` markdown
> line 1
line 2
```

The second line is styled as `<blockquote>` in preview section, but styles as normal paragraph in source section. Because different parser is used in source section and preview section, what I saw in source view may not be inconsistent when is is previewed. This maybe a small issue, but still make me a little upset.

#### Non-Unified styles between source and preview

I appreciate that many markdown editor provide themes for users to choose.  But themes for source window and for preview window is not designed and applied at the same time — they may not fit in when putting together. Sometimes, although code fences are highlighted in both source section and preview section, their color scheme can never be unified. And two different themes or color scheme is too *colorful* and *noisy* to me.

*Therefore, [typora][] is made to get rid of the preview window.*

## Readability and Syntax Highlight

As the article is discussed above, Markdown editors should use better syntax highlight, rather than an independent preview window, to make user’s writings more pretty for reading. And actually Markdown’s most syntax highlight is , naturally, readable, such as headers, bold/italic texts, lists, blockquote and thematic break (`<hr/>`), especially when sytax highlight is supported on most markdown editors.

However, syntax highlight has its limitation on hiding or reducing noisy and useless information behind the real valuable content readers would care. When it goes to image, take `![logo](http://typora.io/img/favicon-128x128.png)` for example, no matter how great the sytax highlight looks like, users cannot accquire usingful information for the text source, instead, we should show the image content to user since that’s what user really care. Not to mention math expressions written by LaTeX, too difficult to tell what it looks like as a formula from highlighted source at first glance. 

{% include image.html img="/assets/un-readble-markdown.png" class="shadow" style="width:500px;" alt="css-theme" caption="Not so readable even when syntax highlight is enabled" %}

In those case, a preview window or preview mode seems to be a must. However, I believe there should be a more lightweight, seamless and distraction-free solution to format, emphasis and display the meaningful content, as a reader rather than writer want, behind its Markdown source.  An even better syntax highlighting or decorating engine is what [typora][] would offer.

## Adapt Markdown Everywhere

*Markdown is so cool, and I want to use it everywhere*, I always feel like that way, like many other guys, after I learned Markdown. But there’re no simple, clean, yet user-friendly markdown textarea for developers. For example, for a to-do app, although not necessary, but the support of markdown could make me feel more comfortable when using it. But how to display user’s input as markdown? Preview window is too heavy, plain text feels cheap and difficult to read when it’s long, while syntax highlighting is noisy and not prefect. Thus my answer is, it should go like this way:

<video src="{{ site.baseurl }}/assets/todo-demo.mov" type="video/h.264" autoplay="autoplay" muted="muted" preload="preload" loop="loop" ></video>

Therefore, [typora][] is a good experiment to create a lightweight markdown input area, which users may not even feel they are inputing marked plain text instead of rich texts. To make that possible, I plan to extract some basic support of markdown and open-source it in future, to make it easier for app to have a lightweight and clean markdown input/textarea.

## How about Texts and FoldingText

They are both awesome products with features (the inline preview) close to [typora][]. But [FoldingText](http://www.foldingtext.com) is a text editor without supports of rich features — such as Images, LaTex and Tables. And only monospaced font is permitted. [Texts](http://www.texts.io), on the other hand, is a mix of rich editor and markdown editor, and sometimes more like a rich editor — one cannot *input* a table, link, image, math expressions or code snippets, but he has to *insert* one from menu or shortcut keys. *So I have to make one from which you can “input" all those rich features using markdown’s syntax formats as it should be.*

## Work With lots of Markdown Flavors

Markdown is so widely used in tech communities, however, it doesn’t have a standardized, unambiguous syntax specification, which leads to many markdown flavors or specifications. As a result, if a writer is not careful enough, his writings might be parsed and rendered differently in different applications or even in same application — once a user complains to me that typora cannot parse the text he wrote by another markdown editor correctly. The content he writes is:

``` markdown
-  list 1
-  
## Header2
```

If you open Mou, and paste it, you will get:

{% include image.html img="/assets/mou-parse-err" alt="" caption=“Same content parsed differently in same application" class="screenshot" %}

Even in same application, markdown will be understood differently by different components. To fix such consequences caused by the ambiguous syntax specification of markdown, some people started the [CommonMark](http://commonmark.org/) project, trying to define a standard, unambiguous syntax specification for Markdown. But it won’t work, if few editors, parsers or websites support it. 

I’m not saying typora will solve this — but it will help reduce the changes that one’s writing is parsed differently once he uses other applications to modify or render the markdown file. The solution is to re-format the whole document when saving:

Unlike some other editors, typora has WYSIWYG features, therefore it is able to understand what user want to get. Take the example above, if user gets 

``` html
<ul>
  <li>list 1<li>
  <li></li>
</ul>
<h2>Header2</h2>
```

in typora’s editing area, then after save he will get:

``` markdown
- list 1
- 

## MPS
```

Also:

``` html
<ul>
  <li>
  	<p>list 1</p>
  <li>
  <li>
  	<p></p>
    <h2>Header2</h2>
  </li>
</ul>
```

will be saved as

``` markdown
- list 1

- 

  ## Header2
```

As I always emphasized — let users focus on the content, rather than get distracted by worrying about different markdown specifications.

## Real Custom Themes

Also, [typora][] use CSS files for custom themes, making it possible for anyone to mark up the writings as they wish. They can change the font size /color for different headers or styles, they can also use Web Font form google, they can add background image for the app, they can add CSS animation when hover or blur, and they can even choose to highlight instead of hide markdown’s syntax instructions (like the `**`) by modifying CSS from `display:none` to `display:inline` to make it act like other markdown editors. More important, after they applied a theme, what they see when writing is almost what they get after exporting to PDF or printing.

{% include image.html img="http://typora.io/img/theme-prev/Snip20150302_23.png" alt="css-theme" caption="Use Css to stylize typora editor" class="screenshot" %}

**So this is the markdown editor I want, and thus I made it, and also hope you would love it!**

[typora]: http://typora.io

[^markdown-principles]: http://daringfireball.net/projects/markdown/
---
title: "Goldmark Typographer issues"
date: 2021-01-29T07:30:00-06:00
lastmod: 2021-11-02T08:28:00-05:00
draft: false
---

# Goldmark Typographer issues

Here are examples of issues found with the `Typographer` extension in the [Goldmark](https://github.com/yuin/goldmark) Markdown parser, which [Hugo](https://gohugo.io) uses. I hope this will help [`@yuin`](https://github.com/yuin) and PR-submitters resolve them; see [this comment](https://github.com/yuin/goldmark/issues/180#issuecomment-769640321).<br />
<span style="font-size: 0.75rem;">Repo for this site: [https://github.com/brycewray/gm-typographer](https://github.com/brycewray/gm-typographer).</span>

For each issue, you'll see:

- The Markdown
- The **correct** result (in U.S. English)
- The current Goldmark/Typographer result

---

## Closing quotation marks within italics

```md
*"At first, things were not clear."*
```

**Correct**:<br />
<em>&ldquo;At first, things were not clear.&rdquo;</em>

**GM/T result**:<br />
*"At first, things were not clear."*

---

## Closing quotation marks within boldfacing

```md
**"At first, things were not clear."**
```

**Correct**:<br />
<strong>&ldquo;At first, things were not clear.&rdquo;</strong>

**GM/T result**:<br />
**"At first, things were not clear."**

---

## Closing quotation marks within boldfacing and italics

```md
***"At first, things were not clear."***
```

**Correct**:<br />
<strong><em>&ldquo;At first, things were not clear.&rdquo;</em></strong>

**GM/T result**:<br />
***"At first, things were not clear."***

---

## Plural possessives

```md
John's dog is named Sam. The Smiths' dog is named Rover.
```

**Correct**:<br />
John&rsquo;s dog is named Sam. The Smiths&rsquo; dog is named Rover.

**GM/T result**:<br />
John's dog is named Sam. The Smiths' dog is named Rover.

---

## Links within quotation marks and parenthetical phrases

```md
This is not difficult (see "[Introduction to Hugo Templating](https://gohugo.io/templates/introduction/)").
```

**Correct**:<br />
This is not difficult (see “[Introduction to Hugo Templating](https://gohugo.io/templates/introduction/)”).

**GM/T result**:<br />
This is not difficult (see "[Introduction to Hugo Templating](https://gohugo.io/templates/introduction/)").

---

## Quotation marks within links

```md
Apple's early Cairo font gave us ["moof" and the "dogcow."](https://www.macworld.com/article/2926184/we-miss-you-clarus-the-dogcow.html)
```

**Correct**:<br />
Apple&rsquo;s early Cairo font gave us <a href="https://www.macworld.com/article/2926184/we-miss-you-clarus-the-dogcow.html">&ldquo;moof&rdquo; and the &ldquo;dogcow.&rdquo;</a>

**GM/T result**:<br />
Apple's early Cairo font gave us ["moof" and the "dogcow."](https://www.macworld.com/article/2926184/we-miss-you-clarus-the-dogcow.html)

---

## Single closing quotation marks with slang/informalities

```md
"I'm not doin' that," Bill said with emphasis.
```

**Correct**:<br />
&ldquo;I&rsquo;m not doin&rsquo; that,&rdquo; Bill said with emphasis.

**GM/T result**:<br />
"I'm not doin' that," Bill said with emphasis.

---

## Closing single quotation marks in quotations-within-quotations

```md
Janet said, "When everything is 'breaking news,' nothing is 'breaking news.'"
```

**Correct**:<br />
Janet said, &ldquo;When everything is &lsquo;breaking news,&rsquo; nothing is &lsquo;breaking news.&rsquo;&rdquo;

**GM/T result**:<br />
Janet said, "When everything is 'breaking news,' nothing is 'breaking news.'"

---

## Opening single quotation marks for abbreviations

```md
We're talking about the internet --- 'net for short.
```

**Correct**:<br />
We&rsquo;re talking about the internet &mdash; &rsquo;net for short.

**GM/T result**:<br />
We're talking about the internet --- 'net for short.

**Note**: This may be impossible to resolve, since it could cause subsequent issues with the opening quotation marks for nested quotes:<br />
`He muttered, "And then she said, 'Hello,' in a shy voice."`

---

## Quotation marks next to footnotes

```md
People ask, "Why can't you just change the format?"[^formatChgNote]
```

**Correct**:<br />
People ask, &ldquo;Why can&rsquo;t you just change the format?&rdquo;<sup style="text-decoration: underline; color: #0000ff;">1</sup>

**GM/T result**:<br />
People ask, "Why can't you just change the format?"[^formatChgNote]

[^formatChgNote]: This is a regular footnote.
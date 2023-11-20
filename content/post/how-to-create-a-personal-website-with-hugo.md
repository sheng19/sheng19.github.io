---
title: "How to Create a Personal Website With Hugo"
date: 2023-11-20T18:47:41+08:00
draft: false
---

## Prerequisites

1. [Install Hugo]
1. [Install Git]

## Create a site

Run these commands to create a Hugo site with the [hugo-theme-stack] theme. The next section provides an explanation of each command.

```bash
hugo new site quickstart
cd quickstart
git init
git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
echo "theme = 'hugo-theme-stack'" >> hugo.toml
```

## Add line numbers to a code block 

```toml
# ./quickstart/hugo.toml
[markup]
  [markup.highlight]
    lineNos = true
```
[Add line numbers]

## Add content 

Add a new page to your site.

```text
hugo new content post/my-first-post.md
```
[hugo-theme-stack]: https://stack.jimmycai.com/guide/getting-started
[Install Git]: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
[Install Hugo]: https://gohugo.io/installation/
[Add line numbers]: https://discourse.gohugo.io/t/am-i-able-to-add-line-numbers-to-a-code-block-despite-the-theme/45966/2
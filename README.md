# devsite

A repo that holds the content for the site [devsquared.space](https://devsquared.space/).

## Theme currently is PaperMod

For more information, see [the wiki](https://github.com/adityatelange/hugo-PaperMod/wiki).

## Manual Process for writing a new post

- create a new markdown file in the posts folder
- copy the front matter from below and modify as needed (can set post to draft if need be)
- write your post
- run the [socialImageMaker](https://github.com/devsquared/socialImageMaker) script to create a new image 
- include this image into the `/images/social` section and reference it in your post
- consider automating all of this :D each time you do it

## Post Front Matter 
```yaml

---
title: "My 1st post"
date: 2020-09-15T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["first"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
image: "<image path/url>" # image path/url
alt: "<alt text>" # alt text
caption: "<text>" # display caption under cover
relative: false # when using page bundles set this to true
hidden: true # only hide on current single page
editPost:
URL: "https://github.com/<path_to_repo>/content"
Text: "Suggest Changes" # edit text
appendFilePath: true # to append file path to Edit link
---
```
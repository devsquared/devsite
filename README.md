# devsite

A repo that holds the content for the site [devinward.me](https://www.devinward.me/).

## Theme currently is PaperMod

For more information, see [the wiki](https://github.com/adityatelange/hugo-PaperMod/wiki).

## Manual Process for writing a new post

- use `hugo new posts/name-of-post.md` to create a new post
- modify the front matter there
- write your post
- run the [socialImageMaker](https://github.com/devsquared/socialImageMaker) script to create a new image 
- include this image into the `/images/social` section and reference it in your post
- consider automating all of this :D each time you do it

To locally see the changes before a deploy, use `hugo server`.

---
layout: post
title: "Site Improvements, pt 2"
author: "Landon"
tags:
- meta
- engineering
---

I've made a couple of recent upgrades and improvements since writing [Jekyll Site Improvements]({% post_url 2018-05-09-site-improvements %}), so I'll go through them here.

## Git LFS
One project that's been sitting on the backburner for this site for a while has been enabling [Git LFS](https://git-lfs.github.com/) - this allows large binaries to be committed by reference, rather than directly included in the repository. I'd been committing all of my large images and pdfs directly into the repository, and it had swelled dangerously close to GitHub's maximum allowed size. It was also very unweildy to get started on a new computer, as it downloaded a full 1.2 GB of files. After enabling Git LFS, the repo weighs in at a mere 11.6 MB. That happened in a few commits, though to rewrite my git history to remove where the large binaries were originally committed, my history got pretty garbled, so I can't link to any specific commits. My [`.gitattributes`](https://github.com/lycarter/blog/blob/master/.gitattributes) file shows the current Git LFS config.

## Hosting in Netlify
Unfortunately, when enabling Git LFS, I completely broke GitHub pages hosting - it's incompatible with Git LFS, which is something I should have realized with just a [tiny bit of Googling](https://github.com/git-lfs/git-lfs/issues/1342). Oops. I searched around for a little bit for hosting options, and eventually settled on [Netlify](https://www.netlify.com/), which has [Git LFS support](https://www.netlify.com/docs/large-media/) as well as very simple configuration and a [solid free tier](https://www.netlify.com/pricing/). For a personal blog like this, I don't really need any of the fancy features that most hosting sites offer, and free is pretty hard to beat. They also ticked a few key boxes like automatic [Jekyll builds](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/) (with just enough configuration to get it to work), and [HTTPS support](https://www.netlify.com/docs/ssl/) through [Let's Encrypt](https://letsencrypt.org/) with super automatic setup. Seriously, I didn't have to touch anything except for my Google Domains DNS settings to get SSL working correctly, and it was on by default. Very much approve.

## Tidying
In transitioning to Netlify, it actually prompted about a few misconfigurations I had, and I learned that I was [using `site.baseurl` incorrectly](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/) in my Liquid syntax (basically, since I serve directly from `/`, and not from, eg, `/blog/`, I don't need to ever use `site.baseurl`).

Thanks for following along. The second ADT post should be coming soon™.

As always, thanks for reading :)
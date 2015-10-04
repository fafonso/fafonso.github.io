---
layout: post
title:  "Working with Jekyll? Get your dev environment!"
date:   2015-10-04 21:00:00
categories: jekyll vagrant puppet
tags: regular
---

In this post I will talk about how you can easily get a development environment with everything you need to run and test your Jekyll site, and all in an isolated VM, how cool is that?!

![ ](/assets/article_images/2015-10-04-vagrant-puppet-jekyll/jekyll.jpg)

Long story short, during my adventure to build this site and learn about how to work with [Jekyll](http://jekyllrb.com), I felt the need to have my own development environment to check my changes and blog posts before send them live to [GitHub](https://pages.github.com/). At the same time, I was playing around with [Vagrant](https://www.vagrantup.com/) and [Puppet](https://puppetlabs.com/) and voilà! I started to work on a project to get a Vagrant VM, using Puppet to  configure everything you need to build and serve you Jekyll site.

![ ](/assets/article_images/2015-10-04-vagrant-puppet-jekyll/vagrant-puppet.png)

All you need to do is to get the project **[here](https://github.com/fafonso/Jekyll-puppet-vm)** and include it in your Jekyll project. Quick notes about that:

- The GitHub readme file of the project will help you setting things up;
- If you are not familiar with Vagrant, it is a good idea to go through this [tuturial](https://docs.vagrantup.com/v2/getting-started/);

Don't miss other cool things I've discovered and some good resources about Jekyll in my [previous blog post]({% post_url 2015-09-13-jekyll-and-more %}).

I hope that you've found this information useful and have fun!
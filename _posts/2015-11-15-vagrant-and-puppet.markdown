---
layout: post
title:  "Configuration Management Tools, let the magic begin!"
date:   2015-11-15 00:18:00
categories: vagrant puppet liferay vm 
tags: regular
image: /assets/article_images/2015-11-15-configuration-management-tools/header_vagrant_puppet.jpg
---
 
I've been talking a little bit about this topic in my previous blog posts, but in the last few months, I've been really impressed with this new (at least for me) configuration management tools thing, and now I'm completely surrendered to it! Therefore I want to share with you my thoughts and experience about this new work approach that can make your life easier, when it comes to getting your specific environment, which is using those technologies with that specific and tricky configuration which you need to do again and again, every time you need to set up your environment, for you or for your team mate.

In this article, I will try to show you the key advantages of using a (or a set of) configuration management tools.

There are lots of new cool technologies in the context of configuration management and virtual environments, tools like [Puppet](https://puppetlabs.com/), [Vagrant](https://www.vagrantup.com/), [Docker](https://www.docker.com/), [Chef](https://www.chef.io/chef/) and so on. 

For my particular case and needs, I've chosen to use **Vagrant with Puppet for provisioning** and now, everytime that I need some new technology or some new specific environment with some particular configuration, I start to think about how can I achieve it using these two technologies. With this approach, I get an easy, portable and consistent way to create my work environments, easily reproducible and with great flexibility: you can start your environment, stop it, do some crazy experiments on it, destroy it and start all over again with just one command line like "Vagrant up".  

![ ](/assets/article_images/2015-11-15-configuration-management-tools/PuppetVagrantVirtualbox.png)

Some key features and aspects of this approach are:

- Using Vagrant with [Virtual Box](https://www.virtualbox.org/), you can get a completly isolated VM where you will be able to install everything you need, leaving your laptop clean and simple, with the minimum set of indispensable software;
- Vagrant offers some really cool and easy to use features like managing the amount of CPU and memory for your VM, port mapping and share folders between host and guest machine;
- Using Vagrant with an [Hashicorp](https://atlas.hashicorp.com) account, you can easily expose your VM over the web and give someone access to your applications, anywhere in the world - Can be useful to show to someone that functionality you've been working on;
- Puppet is a really interesting and flexible technology to handle your system configuration, installing and configuring software, it's just like you are coding your own infrastructure;
- Vagrant and Puppet configuration files are simple, typically small and they can easily be managed with your source in you favorite version control system;
- When you need to install some new software, performe some configurations or just do something with puppet, take a look on [Puppet Forge](https://forge.puppetlabs.com/) first, they have lots of puppet modules that you can leverage on to achieve your end result - Do not reinvent the wheel.

I know that by using these technologies it seems that you will have some overload in your work (because you will need to setup all your puppet and vagrant files), but in the long run, you will end up saving time. You'll only have to setup the environment one time, at the beginning of the project! from there on, all that you need to do is to run a command line and your environment will be recreated all over again from scratch. In the end, you will achieve a less error prone environment, ensuring that all your environments have the same software with the same configurations, easy to share with your team and easy to adapt to new scenarios.

To finish this article, I just want talk a little bit about some of my projects where I'm using these technologies and that you can leverage on to create you own enviroments, try out this technologies or simply take a look on some examples:

- **[Liferay box](https://github.com/fafonso/liferay-puppet-vm)** will give you the option to have a VM running Liferay with some really cool configuration options like: cluster, web server, external SOLR search engine, firewall, and so on;
- **[Jekyll box](https://github.com/fafonso/Jekyll-puppet-vm)** will create for you a VM running Jekyll. I've talked about this project on my [previous blog post]({% post_url 2015-10-04-vagrant-puppet-jekyll %});
- **[Scala box](https://github.com/fafonso/scala-puppet-vm)** is a simple project to creat a VM ready to run your scala scripts.

Places to look for more information:

- If you are not familiar with Vagrant, it is a good idea to go through this [tuturial](https://docs.vagrantup.com/v2/getting-started/);
- [Vagrant and Puppet tutorial](https://puppetlabs.com/blog/puppet-and-vagrant-tutorial).

I hope that you've found this information useful and have fun with your DevOps!

![ ](/assets/article_images/2015-11-15-configuration-management-tools/automate-all.jpg)



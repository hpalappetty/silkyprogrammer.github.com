---
layout: post
title: 'Creating an Authentication Mechanism using gem ''devise'''
tags:
  - devise
  - rails
  - railscasts

---

The obvious choice of place to look for a decent intro to this topic is Ryan's ( Ryan Bate) railscasts.com website.

The link is [[http://railscasts.com/episodes/209-introducing-devise]]

Looks like this link uses an old version of devise, and trying to get it running on your system might waste a lot of time. Nevertheless, the video stands as a good starting point to learn about the implementation of 'devise' for your lovely web app.

my suggesstion is while adding gem 'devise' to your GEMFILE use the following style,

gem 'devise' , 'git://github.com/plataformatec/devise.git' ( this is for people who already have some old devise version on their system)

I have noticed that by replacing the version number against the gem will not help you upgrade it to the latest version.

gem 'devise' '1.1.0rc' ( or something like this you had)

gem 'devise' ( this is what you want to do so that latest stuff gets installed) <strong><span style="color:red;">Won't Work</span></strong>

Remove the old version of devise by running,
$ gem uninstal devise ( on your command prompt)

Then in the gemfile add the following,
gem 'devise' , 'git://github.com/plataformatec/devise.git'

Then follow, the steps described in README(https://github.com/plataformatec/devise/) file along with Ryan's screencast you will be good to go.



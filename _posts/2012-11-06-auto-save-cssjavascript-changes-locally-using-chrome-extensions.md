---
layout: post
title: 'Auto Save CSS/JavaScript Changes Locally using Chrome Extensions'
tags:
  - autosave
  - css
  - javascript
  - livereload
  - tincr
  - web-development

---

For long, I had to make my CSS/JavaScript Changes using my text/code editor save the changes then refresh the browser to see my changes getting reflected.

Voila ! Now there are better ways to do this, they are
<ol>
	<li>Tincr( which I use ) available from http://tin.cr/</li>
	<li>AutoSave (https://github.com/NV/chrome-devtools-autosave)</li>
	<li>Livereload ( costs you $9.99)</li>
</ol>
<strong>Option 1:</strong>

Tincr is pretty easy to set up on Chrome. All we have to do is to install it from Chrome webstore.

For Django developers , configuration may spring a surprise. You will not see any support for Django projects :) but not to worry, just select the configuration file option, and select the "tincr.json" file from the root of your application. A sample tincr.json file is as follows, this file is used by me ( as you can notice that I have added my css &amp; javascript files in media directory)


    `{
    toFile : [
      {from: /media/(.+\\.js),
       to: media/$1},
       {from: /media/(.+\\.css),
       to: /media/$1}
      ],
      fromFile : [
         {from: (\\\\|/)media\\1(.+(\\.js|\\.css))(\\.[a-zA-Z]+)?$,
          to: /media/$2?body=1}
          ]
    }`


You can have the original configuration file from <a title="Tincr Docs" href="http://tin.cr/docs.html" target="_blank">http://tin.cr/docs.html </a>and modify it according to your project directory structure.

<strong>Option 2:</strong>

This is a project being developed by <a title="Nikita's website" href="http://elv1s.ru/" target="_blank">Nikita Vasilyev</a> , a good article on how to set this up is written by <a title="Addy Osmani" href="http://addyosmani.com/blog/autosave-changes-chrome-dev-tools/" target="_blank">Addy Osmani</a>. This is a free tool, and has dependency with Node.js.

<strong>Option 3:</strong>

Livereload is an awesome mac app ( <a title="Live reload website" href="http://livereload.com/" target="_blank">http://livereload.com/</a>) which is available through Mac App Store. It has great support for SASS,Stylus and various other scripting compilers.

Although, it is a great tool. I keep myself away from it due to the fact that it is a paid app ( $10 approx.) and there is no guarantee that I will use it forever in my life. There is no option to try it out as well like Sublime Text, where the author has given unlimited trial period.

The very same team has released a linux version which uses browsers, I haven't tried it though.

So my conclusion, there are plenty of new interesting tools available in the market to release you from the pain of write+save+click refresh :)
Get your hands dirty and try a bit of HTML/CSS/JavaScript, you can become a better web developer the with added skills of making pretty pages.

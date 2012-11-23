---
layout: post
title: 'Django+Heroku is an awesome cuisine!'
tags:
  - django
  - heroku

---

For long I thought heroku is the den built specifically for ruby programmers. Looks like the landscape is changing! Now Djangoer's can peep into the Heroku stack with a wry smile and enjoy the fruits of their work.Today, I am interested in sharing what I learned while deploying my test app to heroku cedar stack.
<ol>
<ol>
<ol>
	<li>A bit of basic python knowledge helps a long way.</li>
	<li>You should have a working Django based application.</li>
	<li>You got to create a file named requirements.txt in your parent directory with all the required software details.</li>
	<li>testapp will reside in a directory <strong>testapp/testapp</strong>, and requirements.txt has to be placed in the parent testapp directory.</li>
	<li>Create a virtualenv within your application directory by typing $ virtualenv venv --distributable</li>
	<li>Run the command pip intall -r requirements.txt</li>
	<li>My requirements.txt looks have the following content,</li>
</ol>
</ol>
</ol>
[sourcecode language="css"]
Django==1.4.1
South
psycopg2==2.4.5
dj-database-url==0.2.0
Flask==0.9
[/sourcecode]
<ol>
	<li>Add all the files to git. ( so a github account is essential, if you wannabe a good social coder.)</li>
[sourcecode language="css"]
$git init
$git add .
$git commit -m &quot;commits&quot; ( if you dont have git configured on your system, the above commands wont work well)
$git push
[/sourcecode]

	<li>Push your application to the heroku stack <strong>$ git push heroku master</strong></li>
	<li>Run your server using heroku South <strong>$heroku run python manage.py/runserver</strong></li>
	<li><strong>SyncDB</strong> before opening the website. Here is the catch, you got to setup your postgres DB instance on heroku. You can do that by login to <strong>https://postgres.heroku.com</strong> . NO PAYMENTS, but they might take your credit card details for account verification, but no charges.I found this a bit annoying, if I am not charged then why the heck  do I have to give away my Credit card details.I am just testing the stuff dude. Anyway, the end result is good, so no cribbing. Heroku, will give you the DATABASE details to be pasted in your <strong>settings.py</strong> file, it will look something like this,</li>
</ol>
[sourcecode language="css"]
 DATABASES = {
'default': {
'ENGINE': 'django.db.backends.postgresql_psycopg2',
'NAME': 'd32333645f',
'HOST': 'asdasasdasdasd.compute-1.amazonaws.com',
'PORT': 5432,
'USER': 'asdasdasdasda',
'PASSWORD': 'ASADSADSADASDASDASD'
}
}
[/sourcecode]
<ol>
	<li>Once you paste the above details to your settings.py ,  add the files to git again and then push master branch to heroku stack.This will keep heroku up to date.</li>
	<li>Run<strong> heroku run python manage.py syncdb , </strong>this will set up your DB on heroku stack.</li>
	<li>See your cool website by typing in <strong>heroku open</strong></li>
	<li>Enjoy django development on heroku.</li>
</ol>

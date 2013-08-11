---
'layout' : 'post'
'title' : 'How can you deploy a simple django application on heroku with postgresql as db?'
---
<p>This article explains "As a developer what you need to do"  to install a simple Django application on heroku stack ($0 priced stack).</p>

<p>I will explain the problems faced during this process, some tips as well to get this working.</p>

<p>What your setup should be like</p>
<blockquote>
<ul>
    <li>A *Nix based system</li>
    <li>Python must be installed</li>
    <li>You should have pip and distribute installed</li>
    <li>You must have heroku tool-belt installed</li>
    <li>You must have postgresql installed</li>
</ul>
</blockquote>

<p> Once the above list is checked you can create a folder with your app name in project directory.In my case it is in HOME/projects</p>
        $cd ~/projects
        $mkdir todolist
        $cd todolist

<p>At this point, we may want to create a project with specific version of Python or Django. To do this, we must install virtualevn. This can be done by downloading the 
package from Python package index [virtualenv]:(https://pypi.python.org/pypi/virtualenv). Once you download the package from this location, extract the same
and then</p>
        $ cd ~/Downloads/virtualenv-1.10.1/
        $ sudo python setup.py install

<p>This will install the virtualenv to your system. After this create a virtualenv in your application folder.</p>
        $ cd ~/projects/todolist
        $ virtualenv venv --distribute
        $ source venv/bin/activate

<p>After this we can create a django project by</p>
        $ django-admin.py startproject todolist

<p>Then move to your project root folder by </p>
        $ cd todolist
<p>then</p>
        $pip freeze > requirements.txt

<p>Once the above set up is complete, we can complete the settings in settings.py file.This is a tricky area, and is the point where most of the newbies near Heroku
gets stopped. To deploy a django app to heroku, you have to login to your heroku account and then add Heroku-Postgres addon (dev version) which is free.You can get the
details of DATABASE from heroku account and then add those details to your settings file, it will look similar to what I have posted below.</p>
        DATABASES = {
            'default': {
                    'ENGINE': 'django.db.backends.postgresql_psycopg2',
                    'NAME': 'daskhdhlklkll',
                    'USER': 'dtoasdashasaabh',
                    'PASSWORD': 'OmasdjasLKJJJKSDkjsakajskja5d-',
                    'HOST': 'ec2-94-111-212-45.cxxxxxx-1.amazonaws.com',
                    'PORT': '5432',
                    }
            }

<p>Once the above details are set it's time to enjoy deploying your app to heroku platform.To complete the steps, first we have to put the code in 'git' first.
Then push the code to heroku.Create a 'Procfile'at the root of your application and add a webworker to it. This is explained well in heroku documentation, so I am not explaining it again.
We also have to create a heroku stack, which can be done before adding the code to git.</p>
        
        $cd ~/projects/todolist/todolist
        $heroku create ( will ask for your heroku credentials)
        $git init
        $git add .
        $git commit -m "my first heroku application"
        $git push heroku master

<p>During this process , heroku will ask for your user name and password.Please provide appropriate credentials.</p>

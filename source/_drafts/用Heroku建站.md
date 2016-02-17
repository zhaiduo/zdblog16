---
title: 用Heroku建站
tags:
  - Cloud
  - 'Ruby &amp; Rails'
  - git
id: 1208
categories:
  - 网站技术
---

install ruby192

install rails stand-alone
http://rubyforge.org/frs/download.php/63167/rails-2.3.4.gem

gem install rails
gem install heroku

rails new zdcms
heroku create zdcms

cd zdcms
git init

git add .
git commit -n 'fisrt cm'

git remote add heroku git@heroku.com:appname.git

git push heroku master

next: http://guides.rubyonrails.org/getting_started.html

    1  git clone -o heroku git@heroku.com:zdcms.git

   25  script/generate controller home index
   26  git add .
   27  git commit -m 'generate controller home index'
   28  git push heroku master
   29  git commit -a -m 'generate controller home index'
   30  git push heroku master
   31  git push --help
   32  git push --help

   34  cd zdcms
   35  git push heroku
   36  git -f push heroku master
   37  git push -f heroku master
   38  git commit -a -m 'add .gems'
   39  git add .
   40  git commit -m 'add .gems'
   41  git push heroku
   42  heroku ps
   43  git commit -a -m 'update routes.rb'
   44  git push heroku
   45  heroku ps
   46  heroku logs
   47  heroku logs
   48  git commit -a -m 'update routes.rb'
   49  git push heroku
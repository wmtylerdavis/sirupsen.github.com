---
layout: post
title: SQLite to Postgres
tags: 
---
Currently I’m trying to learn some Rails by going through Michael Hartl’s wonderful Rails Tutorial. I decided a little late in the game that I wanted to change my development and test databases from SQLite3 to the same as my production Heroku friendly Postgres database. 

So I downloaded Postgres, had a few hiccups but nothing Stack Overflow couldn’t handle, changed my database.yml file to something akin to this:

    development:  
    adapter: postgresql  
    encoding: unicode  
    database: myapp_development  
    pool: 5  
    username: username  
    password:
    
    test:  
    adapter: postgresql  
    encoding: unicode  
    database: myapp_test  
    pool: 5  
    username: username  
    password:
    
    production:  
    adapter: postgresql  
    encoding: unicode  
    database: myapp_production  
    pool: 5  
    username: username  
    password:
    
I ran bundle exec rake db:create:all, and I was off to the races. Creating users in the console seemed fine… except it wasn’t. Days go by and I finally figure out that I can’t find my users. I’m not sure why but my .sqlite3 database files were still in the app. So I removed them. Ran a db:migrate. Hmm… still not working. 
Another Google and SO search and boom: bundle exec rake db:reset
This tiny command saved me lots of heartache. 

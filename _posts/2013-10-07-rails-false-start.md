---
layout: post
title: "Rails False Start"
tags:
- programming
- ruby
---

I finally got a little bit of time to work on Lunch Push this weekend. Of course I got that anxious feeling of opening up a project you haven't looked at in a while. The heart pounding anxious feeling of not know where you left off and where to start back.
 
Yeah, then I just checked my commit messages and all was well. I had left off with creating Lunch and Restaurant models. So I added a few test for these models and then I decided to jump into creating their controllers. So while I got a decent bit working I definitely fell into a pitfall that I've decided to rework next weekend.
 
###What I Did
 
See what had happened was... I still have this whole Twitter, I mean Micropost, mentality. So I'm thinking that each Lunch should have restaurants and that users should just be able to create restaurants on the fly with a name and website. It's simplistic and it would work in the short term. It's not like I'm planning on having thousands of users. I know that I'm going to have like maybe 10 users - my friends and coworkers. So why not keep this model and press?
 
Well restaurants are pretty static. I can get a list of restaurants from a multitude of APIs: Yelp, Foursquare, Google, etc. So why should users have to type them in? That would be tedious.
 
###The Plan
 
First and foremost I'll actually split out the views for Lunches. No longer will a Lunch just have a show view. Instead it will have at least a new view which will ask for the zip code. Later on it may ask for emails of coworkers so that it can mail out the lunch request.
 
Next I'm going to separate out Restaurants from Lunches. One a Restaurant is created, it should stay in the database. This should dramatically reduce the database size in the long run. I can then use has_many :through.
 
I'm probably going to model it out this way:
{% highlight ruby %}
    class Lunch < ActiveRecord::Base
      has_many :lunch_locations
      has_many :restaurants, through: :lunch_locations
    end
 
    class LunchLocations < ActiveRecord::Base
      belongs_to :lunch
      belongs_to :restaurant
    end
 
    class Restaurant < ActiveRecord::Base
      has_many :lunch_locations
      has_many :lunches, through: :lunch_locations
    en
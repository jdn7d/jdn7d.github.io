---
layout: post
title:      "Relationship Problems - Sinatra Project "
date:       2020-10-07 00:44:42 +0000
permalink:  relationship_problems_-_sinatra_project
---

First, I must congratulate myself because this project went much more smoothly than the first project. I went into the project with a better understanding of the material than I did for the CLI project and I took a lot more time with planning before I started coding. My project is title FlatFile. A flatfile is a cabinet with shallow drawers that you use to store art. A user would use my application to remember and keep track of artists and artworks they find interesting. To build this app I started with Users, Artists, Artworks and UserArtists tables and models. I also had Users, Artists, and Artworks controllers and views folders associated with each of those.

When planning my model relationships and migrations, I decided that Users and Artists would need to be in a many to many relationships, because technically multiple users can add the same artists. I first coded my project using a join table titled UserArtists.

Using join tables can be tricky because you must pay close attention to pluralization. My artists weren't saving correctly, and I realized I needed to delete the UserArtists table and add a UsersArtists table. 

I deleted: 

```
class CreateUserArtists < ActiveRecord::Migration[6.0]
  def change
    create_table :user_artists do |t|
      t.integer :user_id
      t.integer :artist_id
      t.timestamps null: false
    end
  end
end

```

and I added: 

```
class CreateUsersArtists < ActiveRecord::Migration[6.0]
  def change
    create_table :users_artists do |t|
      t.integer :user_id
      t.integer :artist_id
      t.timestamps null: false
    end
  end
end

```

Most of the documentation and examples that I had referenced online only pluralized the last word of the join table title. However, through trial and error I finally settled on UsersArtists. All was good. Until... 
After feeling like I had finished all the functionality of my project, I created a user and added an artist name that I had added to a different user’s account. When I clicked on the artist to add an artwork, there were already 3 artworks saved! I had a moment of panic because I had spent so much time figuring out the join table to save the users and artists correctly. After a few hours of contemplating how to fix this issue, I finally decided that although different users could save the "same" artist, each user can add unique artists, with their own notes about the artist. In this case all I had to do was delete the join table, remove that relationship from my models and add user_id to my Artists table. After making this change, the artworks saved to that unique instance of the artist. 

Next time, I know to consider the relationships more thoroughly, but I will also know how to utilize a join table if need be. 


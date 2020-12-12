---
layout: post
title:      "Rails - One Form Three Views "
date:       2020-12-12 17:24:35 -0500
permalink:  rails_-_one_form_three_views
---


My roommate recently bought a new house. As someone who has been passionate about interior design since I was a teenager, I was immediately inspired by the large empty rooms and blank walls. As I decided how I wanted my bedroom in the house to look, and helped my roommate design multiple rooms in the house, I ended up with dozens of tabs open on my phone and laptop while research and shopping. I decided to create DSGNR, to have a place to keep track of stores, pieces and inspiration photos that I find online. 

In this app, the designer creates an account. Then the designer can add room objects and for each room, there are pieces and inspiration photos. Designers also add stores, and pieces belong to a store. For this project I utilized 3 nested routes, to accomodate for these associations. 

```
resources :rooms do
    resources :pieces
 end
 
 resources :rooms do
    resources :reference_photos
 end

 resources :stores do
    resources :pieces, only: [:index, :show, :new, :edit]
 end
```

When creating piece and reference photo instances, the user inputs information and selects from drop down boxes. The drop downs are populated with the options_from_collection_for_select method. Using this method is fairly straightforward: 

```
 <%= f.select :room_id, options_from_collection_for_select(@rooms, :id, :name) %>
```

Then, when editing the piece or reference photo instances, all the data is auto populated for that instance. However, I noticed that the method, as it is written above, always defaults to the first option in the drop down. Since all the information autopolulated except for the drop downs, I found a way to default to the correct option for that instance. The fourth attribute in the options_from_collection_for_select method is the default value as shown below.  

```
  <%= f.select :room_id, options_from_collection_for_select(@rooms, :id, :name, @piece.room.id.to_i) %> <br>
  
```

Pro-Tip: The ID must be converted into an integer for the default value to work properly. 

Then after going to the nested routes, I decided that I want the form to adjust to that nested route. If you navigate to a the new piece form from a specific room or store, I didn't want that drop down option to appear at all. After trial and error, I found that the code below accounts for 3 types of forms, new, edit and nested new. 

```
   <% if @room %>
      <%= f.hidden_field :room_id, :value => @room.id %>

   <% elsif @piece.name %>
        <%= f.label :room_id %>
        <%= f.select :room_id, options_from_collection_for_select(@rooms, :id, :name, @piece.room.id.to_i) %> <br>
    <%else %>
      <%= f.label :room_id %>
      <%= f.select :room_id, options_from_collection_for_select(@rooms, :id, :name) %> <br>
   <% end %>
```

This if statement covers all three views that I want from the same form! 



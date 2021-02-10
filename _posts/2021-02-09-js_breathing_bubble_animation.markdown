---
layout: post
title:      "JS Breathing Bubble Animation"
date:       2021-02-10 02:10:50 +0000
permalink:  js_breathing_bubble_animation
---

In my guided meditation app, Pause, I incorporated an animated breathing cirlce in my project. I first used CSS to create the animation, by grabbing some code online, If was fairly simple to get the bubble to expand and shrink on an interval, but I needed the animation to start, pause and end with the event listeners that I already created. I decided that I wanted to use pure Javascript to build this animation. 

To acheive this, I created two methods, expand() and shrink(), to control the increase and descrease in width and height of the circle. I tried combining these methods, but since I wanted the bubble to change the direction of motion, at the same time the text changed on the screen, I found that two methods worked best. The script appeared and changed on screen with an "if" statement. I decided I could have the expand and shrink methods alternate, by seeing if the index of the script array was even or odd.

For context, this is the method that starts the script and the bubble animation. 

```
   function playContent(parsedContent, i) {
            
            medDisplay.innerText = parsedContent[i["count"]]
            
             if (i["count"]%2 === 0) {
               expand()     
             }
             else {
               shrink() 
             }
            i["count"] +=1
            if (i["count"] > (parsedContent.length)) {  
               meditationEnd(showMeditation, meditation)   
            }
         }
```

You can see that I used the value of count, to oscillate between expanding and shrinking the bubble. Then in the following two methods, I have the code that actually adjusts the size of the bubble with pure JS:

```
function expand() {
       let size = 100
         var id = setInterval(frame, 36)
         function frame() {
            if (size == 197) {
               clearInterval(id) 
            } else {
            size ++
            bubble.style.height = size + 'px'
            bubble.style.width = size + 'px'
            }
          }
         
         }
      function shrink() {
         let size = 197
         var id = setInterval(frame, 36)
         function frame() { 
            if (size == 100) {
               clearInterval(id)
            } else {   
            size = size - 1
            bubble.style.height = size + 'px'
            bubble.style.width = size + 'px'
            }
         }
      }
```

To create this animation, I started the bubble with specific dimensions, and then added 1 pixel to the height and width, until it was my preferred max height. I had to make sure that I set the correct initial "size" value, otherwise the transitions from expand to shrink, and vice versa, would be smooth.  



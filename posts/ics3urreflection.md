# ICS3UR Culminating Reflection

---

# Planning Documentation

The planning week is arguably one of the most important parts of this culminating assignment, it helped us plan, organize and create, this also helped me visualize what variables I may want to use in the future, these variables covered everything from how many chips players should start off with, to how I would process images within my code for ease of access, I knew I needed an easy way to access images since it was the most important part of my code, I needed a place to store the positions of the symbols, and needed a way to access images easily instead of writing the name of each image manually when it was called upon, for this situation I had a clever idea that was used in my last coding project for this course, an array for images, this array allowed me to call any images I would like with simply only using numbers, and not typing out the full name everytime, with planning on making this adjustment when I start to write my code, I knew I would save myself not only time, but effort, I could save my energy to focus on other challenging topics throughout my code to manage my time wisely, as we have limited class time to use, and I was planning on using each day as effectively as possible to maximize completion, I know if I don’t use methods to ease my experience in coding, I would start to fall behind in progress, and some elements I mentionned would be added would maybe have not been for when the project was due. For this week I also used a smart way to manage my time, a Gantt chart, this helped me plan ahead to avoid scheduling conflicts, and decide what I will do on the days we have, again to maximize my completion rate of my awaited slot machine game. I also made a method chart, so I could easily reference methods I need to use when we start actually coding, lastly I created mock GUI for multiple pages of my game, like a starting screen, main menu and ending screen, so I could really visualize what I wanted the project to look like when we commenced coding.

# Repition Structure

The loop implementation I will be choosing to explain is the most important loop I will use and currently use throughout my code, in the snippet of my for loop below, you can see that I use another for loop inside of a for loop, these two loops are used to make the positions for where symbols will be placed with the rows and columns of the slot machine, the loop runs to where it also places the images into the predetermined positions by referencing the images from an array that was discussed in Variables & Data Tracking, I used an array to store the image used, so in the future, it will be easier to cross reference to see if a player filled a row or column on the slot machine. To make sure the spacing of the images was correct, I firstly make the X value of the image, equivalent to 350 + which iteration the loop was on, multiplied by 185 which after trial and error, I figured out was an equal distance for each box of the slot machine, not only did I have to make the symbols go horizontally, they also needed to go down vertically for the columns, in which I used a very similar method, where I used 150 as my base, plus which iteration of the for loop for rows was on multiplied by 160, after multiple attempts of trial and error, I was able to get these values, that make the game look symmetrical and even. The snippet of the for loop is down below:

int r = 0;
for (int row = 0; row < 4; row++) { // for loop to randomize row image numbers
    for (int col = 0; col < 5; col++) { // same thing but for columns
      image(imgs[symbols[r]], 350 + col * 185, 150 + row * 160); // makes the images 	line up with all the boxes
      r++;
    }    
  }
}

# Arrays & Data Structures

An important array I used that is referenced throughout my code is my image array, on the first day of coding, I created this array for ease of access as discussed in the planning documentation section, this helped me access images without having to reference them manually every time I wanted to use them, and because I use a lot of images for symbols throughout my slot machine game, this was a necessary feature for my code, but there were also other reasons this decision helped me and is still currently helping me, working in class on my code on Tuesday, a couple of classmates had mentioned that the probability was extremely low on creating winning rows and columns, seeing this as a vital issue, as no player wants to play a game where they would never win, I created a vital solution to this issue, making the probabilities for each symbol would be extremely hard, and would take a lot of extra code, instead I had an idea that was not only easier, but also more efficient, I created multiple of the same images in the array, you may be thinking that I created one image twice to double the odds, but instead I wanted to have a fair playing field throughout all symbols, so I decided to create 100 extra images, I decided that I wanted to split a percentage to all the possible symbols, for example, many of the fruits have a 10% chance of appearing, while rarer items like sevens have a 3% chance of dropping, this was used to ensure fairer odds and keep players interested in the game while also keeping them engaged and not letting them win every time the lever was pulled down.

PImage[] imgs = new PImage[102]; // 100 images for symbols, 1 for the starting screen and one for the background of the main menu

symbols[i] = int(random(1, 101));

# Selection Structures

In my game, I used control structures in multiple places as necessary, for example one problem I faced was when I needed a way for users to add or subtract from their bet, an easy way I found a solution was to use processings built in function for checking mouse inputs, when players left click on their mouse in a specific area, the bet increases while if they right click, the bet decreases, this was to insure easy use within the user. Implementing this idea originally was not that easy, at first I used the mousePressed function, and used an if statement within the mousePressed method that checks if the user is clicking within the area of the circle, even though this is a solution, I didn’t really like it because it removed a lot of the bet at once, instead of intervals of 20 chips per click, that’s when I decided to implement my new idea, which then worked, when players click, it only removes 20 chips per left click or right click, even though this method takes users longer to increase the bet to the desired value, with the other method, you wouldn't be able to stop the bet on the users desired value, because it would increase and decrease the bet too fast when clicking.

 if (mousePressed && mouseX > 1275 && mouseX < 1375 && mouseY > 680 && mouseY < 780 && startGame) {
   if (mouseButton == LEFT && betamount < chips && betamount < 999) {
      betamount += 20;
    } else if (mouseButton == RIGHT && betamount > 20) {
      betamount -= 20;
    }
  }


# Use of Custom Functions & Error Checking/Restrictions

callSymbols() - A key method used throughout my code, this method fills the symbols[] array with random values that represent the icons shown on the machine, which makes the for loop run continuously while the lever is down for a duration of 3 seconds using the millis feature.

checkWin() - Detects winning rows or columns, it scans the 4x5 grid after the reels stop spinning and checks if the player has connected symbols vertically or horizontally. It stops immediately after detecting a win, preventing multiple payouts from the same spin.

startScreen() - Controls the lever, betting system and when the game is allowed to start. It uses constrain() to make sure the lever cannot go to high or to low, prevents the player from spinning if they don't have enough chips (chips >= betamount), prevents the lever from being spun twice (leverLocked = true), also ensures the bet amount never drops below 20. 

These methods didn’t work at first, but after multiple attempts of trial and error, they managed to function and are now a crucial part of my code.

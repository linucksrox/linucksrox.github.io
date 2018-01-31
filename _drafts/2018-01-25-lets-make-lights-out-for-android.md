---
title: "Let's Make Lights Out for Android"
date: "2018-01-25 13:15:24 -0500"
categories: android letsmake
---

I've always enjoyed the classic game Lights Out by Tiger Electronics. It's a fairly simple idea: there is a grid of 25 buttons which can be lit or not lit. When you press a button, it just toggles the light for the button you pressed plus any adjacent buttons. So you would start with a randomized board (or predetermined pattern), and the goal is to turn off all the lights while pressing the fewest buttons possible.  
![](/assets/images/tiger-lights-out.jpg)

Ok, maybe I'm one of only 4 people who think this is cool, but either way it's a good starter project, so let's make it for Android!

## 1. Create a new project
- Click Start a new Android Studio project.  
![](/assets/images/letsmakeandroidlogicpuzzle1.png)
- Set up your project.  
![](/assets/images/letsmakeandroidlogicpuzzle2.png)
  1. Name your app.
  2. Your personal/business domain (can be anything, but should be unique so that the app's name doesn't conflict with an app with the same name in places like the Play store).
  3. Where are you storing your project? I recommend creating a folder for Android projects.
  4. Click Next.
- Unless you have a specific use case, just use the default settings for Target Android Devices. Click Next.  
![](/assets/images/letsmakeandroidlogicpuzzle3.png)
- We just need an empty activity for now, so click Next.  
![](/assets/images/letsmakeandroidlogicpuzzle4.png)
- I'll use the defaults for now. As apps get more complicated we start thinking of better names to organize everything. For now, keep the defaults and click Finish.    
![](/assets/images/letsmakeandroidlogicpuzzle5.png)
- Wait while android builds the project.  
![](/assets/images/letsmakeandroidlogicpuzzle6.png)
- Expand app/java/com.domain.appname and app/res/layout to find the MainActivity.java and activity_main.xml files to get started.
![](/assets/images/letsmakeandroidlogicpuzzle7.png)

## 2. Create a layout

---
title: "Let's Make Lights Out for Android Part 1 - Creating the Layout"
date: "2018-02-02"
categories: android letsmake
---

I've always enjoyed the classic game Lights Out by Tiger Electronics. It's a fairly simple idea: there is a grid of 25 buttons which can be lit or not lit. When you press a button, it just toggles the light for the button you pressed plus any adjacent buttons. So you would start with a randomized board (or predetermined pattern), and the goal is to turn off all the lights while pressing the fewest buttons possible.
![](/assets/images/tiger-lights-out.jpg)

Ok, maybe I'm one of only 4 people who think this is cool, but either way it's a good starter project, so let's make it for Android!

The end goal here is to demonstrate how to create a simple game from scratch, add some features, refactor the code, and eventually release it on the Google Play store. I'll walk through every step start to finish, so you should be able to follow along even if you're new to Android or Java.

For reference, [here is the current state of the project on Github.](https://github.com/linucksrox/AndroidLogicPuzzle)

## 1. Create a new project
- Click Start a new Android Studio project.  
![](/assets/images/letsmakeandroidlogicpuzzle1.png)
- Set up your project.  
![](/assets/images/letsmakeandroidlogicpuzzle2.png)
  1. Name your app. I'll go with Lights Out.
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
Our layout is going to be very basic at this point, because we just want to show a grid of buttons that we can start interacting with. We'll focus on tweaking the layout later on after implementing some of the functionality. I like to focus on getting things functional before worrying too much about how it looks.

As you might know already, there are a bazillion ways to do layouts, and I'm just focused on showing something that's very simple for two reasons:  
1. It should be simple to understand.  
2. It shouldn't take too much effort to feel like you're making progress.

- Open the provided layout file activity_main.xml. They start you out with a single TextView inside a layout, but we'll completely replace that with our own layout.
There are a few things to note here:
1. The outer RelativeLayout uses a vertical orientation, which means that each element can be placed relative to the outer edges and relative to each other. In this case, every inner LinearLayout represents one row of buttons from top to bottom.
2. The outer RelativeLayout has layout_gravity set to center_horizontal, meaning the entire grid of buttons will be centered on the screen horizontally.
3. The inner LinearLayouts (each row of buttons) have their orientation set to horizontal, meaning each element inside of them (each button) is placed left to right.
4. We set the layout_width and layout_height of every button to the same value - buttonWidth - so that every button is a square. We might change this later on so that buttons dynamically shrink or expand depending on screen size, but this method is a little easier for now.
5. The button background is set to whatever color we assign to colorLightOff, which will be light gray.
6. The button layout_margin is set to the value of buttonSpacing, which just separates each button by a little bit so they're not all right next to each other.

We'll define the dimensions and colors next, so don't worry about any errors you see after pasting this into your layout.

~~~ xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:layout_gravity="center_horizontal">

    <LinearLayout
        android:id="@+id/buttonRowA"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_above="@id/buttonRowB">

        <Button
            android:id="@+id/a0"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/a1"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/a2"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/a3"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/a4"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>

    </LinearLayout>

    <LinearLayout
        android:id="@+id/buttonRowB"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_above="@id/buttonRowC">

        <Button
            android:id="@+id/b0"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/b1"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/b2"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/b3"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/b4"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>

    </LinearLayout>

    <LinearLayout
        android:id="@+id/buttonRowC"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_above="@+id/buttonRowD">

        <Button
            android:id="@+id/c0"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/c1"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/c2"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/c3"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/c4"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>

    </LinearLayout>

    <LinearLayout
        android:id="@+id/buttonRowD"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_above="@+id/buttonRowE">

        <Button
            android:id="@+id/d0"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/d1"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/d2"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/d3"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/d4"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>

    </LinearLayout>

    <LinearLayout
        android:id="@+id/buttonRowE"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_alignParentBottom="true"
        android:paddingBottom="10dp">

        <Button
            android:id="@+id/e0"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/e1"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/e2"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/e3"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>
        <Button
            android:id="@+id/e4"
            android:layout_width="@dimen/buttonWidth"
            android:layout_height="@dimen/buttonWidth"
            android:background="@color/colorLightOff"
            android:layout_margin="@dimen/buttonSpacing"/>

    </LinearLayout>

</RelativeLayout>
~~~

- You probably noticed that there are some values we just referenced that don't exist, so we need to create those. We need to define the buttonWidth and buttonSpacing dimensions and the colorLightOn/colorLightOff colors. Starting with the dimensions, right click on app->res->values, and click New->Values resource file. Name it dimensions and click OK.
![](/assets/images/new-values-resource.png)
![](/assets/images/new-dimensions-file.png)
- Open dimensions.xml (the one you just created), and add a dimension element named buttonWidth, setting the value to 60dp. Also add buttonSpacing, setting its value to 2dp. You can tweak these to your liking a little bit later.

~~~ xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="buttonWidth">50dp</dimen>
    <dimen name="buttonSpacing">2dp</dimen>
</resources>
~~~

- Next, we need to define some colors for the lights when they're on or off. Open app->resources->values->colors.xml (this was already provided for you when you created your project). Add the two colors named colorLightOn and colorLightOff, leaving the existing colors which are used in other parts of the app.

~~~ xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="colorLightOn">#FF2222</color>
    <color name="colorLightOff">#AAAAAA</color>
</resources>
~~~

- Back in the layout preview or layout design mode, you should now see the grid pattern.
![](/assets/images/button-grid.png)

Congratulations! You made a button grid layout, and you can tweak the colors or dimensions however you want before continuing on to the next part where we'll hook up the logic and actually toggle the lights on and off when you press the buttons.

Leave a comment if you have any questions or want me to elaborate on anything.

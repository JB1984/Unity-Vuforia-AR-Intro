# Unity Vuforia AR Intro

<h3> Required software and knowledge </h3>

This repository is an intro tutorial for people interested in starting to use Unity and Vuforia for AR applications.

I am going to assume that you have Unity already installed on your computer and that you have a basic level of understanding of the Unity editor and C# scripting. In this tutorial we do not do anything too complex with either the editor or scripting so dont worry if you are still relatively new.

If you do not have Unity installed go to www.unity3d.com and install it. As I write this the latest version of Unity for Windows is 5.5.1f1

Next thing that you will need is the Vuforia SDK for Unity. Go to https://developer.vuforia.com/ and register for a free account. Once you have an account and are signed in go the "Downloads" tab choose the "SDK" tab undearneath that. You will want to "Download for Unity", as I write this the latest Vuforia version is 6.2.10.

<hr> </hr>

<h3> Basic Unity Vuforia setup </h3>

The app that we are creating is going to be very simple. It will recognize a specific image that you have given it and then will place a Unity GameObject on top of that image in the AR scene. This is the most basic AR app that you can make but it was a starting point for me and also I think that it is a great place for you to start as well because it gives you the basics of how to make a Unity Vuforia AR scene and you can just build on it from there to make complex apps.

One last thing to note, I am going to be making this app for Android. So if you have an Android phone and you have it in developer mode enabled then you can build and test this app using your phone straight from Unity.

Open up Unity and create a new 3D project, name it whatever you want. I am going to name mine "ARTutorialBasics". 

Now lets grab the Core Features samples package from the Vuforia website. Go to https://developer.vuforia.com/ click on the "Downloads" tab and choose the "Samples" tab underneath that. Look for the "Core Features" and then click "Download for Unity". This will give you a .zip file with the basic components that you will need to create this VR app. You will notice that there are a lot of really cool Core Features in the Vuforia SDK but for this very basic starter app we are only going to be concerned with "Image Targets". In later tutorials we will go through more of the Core Features and also use some of the features listed in the "Advanced Topics" samples.

Once the "Core Feature" has downloaded lets create a new folder on the desktop to hold the .zip contents. I am going to name mine VuforiaSamples but feel free to name the folder whatever you want. Unzip the contents of the file you downloaded to this folder you just made. It should contain two unity files, one called "ImageTargets" and another "VuforiaSamples".

Lets go back to Unity now and click on the Assets tab of the Unity toolbar. Go to "Import Package", and then "Custom Package". Click on this and navigate to the folder we just made with the Vuforia Core Feature samples. Select and open the "VuforiaSamples". Unity will decompress and import the items of this file. You will then be given a pop-up with the option to select files. Make sure that all of the items are selected and then hit Import.

We are almost done with the basic Vuforia setup.

Lets do one last thing. In all Vuforia applications we do not use the standard "Main Camera" that is provided to us by Unity. We use a special ARCamera prefab that comes with Vuforia. So lets first delete the "Main Camera" from the current Scene Hierachy. We will see a "No Cameras Rendering" in the game view, thats fine. Lets now navigate in the Project area of Unity to the "Vuforia" folder, and click the dropdown arrow next to it. Now select the "Prefabs" folder. You will see a prefab in this folder called "ARCamera" drag and drop this in to your Unity scene. In the cameras Transform component change the rotation of X to be 90. Leave the "World Center Mode" to be "FIRST_TARGET". 

<h3> Vuforia license key</h3>

Now lets click on the "Open Vuforia configuration" button, this configuration menu we are opening up is very useful and we will use it many times going forward so just remember that it is attached to the ARcamera GameObject. Now that we have the Vuforia Configuration open we can input our Vuforia App License key. Without putting a key here when we try and run the app we will recieve a "no key found" error and we will not be able to run the app.

Ok so lets go back to the Vuforia website, making sure that you are logged in. Click on the "Develop" tab and then the "license Manager" sub tab. You will see a button called "Add License Key", click on this. You will need to select a project type, you should select the type that fits your porject but just know that all keys other than "Development" require money to use. You can develop using Vuforia at no cost. So that is what we are going to do, select the "Development" type for your app. Give your App a name and then click "Next". You will be asked to confirm the items so check the confirm box and hit the "confirm" button. You will now see the app listed in your License Manager menu. Click on this app name.

You will now be at a page that lists your license key. Copy the key and then go back to Unity.

In Unity select your ARCamera GameObject and then click the "Open Vuforia configuratoin". At the top of this menu you will see a blank box where you can input your App license key. Copy and paste your Vuforia license key here and then save your project.

<h3> Image for ImageTarget </h3>

Ok so now that we have the fundamental setup of our AR app in place lets set up an image for the ImageTarget. An ImageTarget is simply a GameObject that has an image attached to it. When your app see's that image through the camera of whatever device you are running the app on it will trigger an action to take place. It our app that action is simply going to be to instantiate another GameObject in our scene. We are going to have it instantiate a sphere just for simplicity, but know that it can be any GameOjbect.

So the first thing we are going to do is go back to the Vuforia website and back to the "Develop" tab and select the "Target Manager" sub tab. Vuforia works off of databases of images that we use as ImageTargets. We can have a database of one image, as is the case with our app, or thousands for more complicated apps. We want to create a new database for our app so we hit the "Add Database" button. For simplicity we are going to make this a "Device" database type so select this option. We could make it in the cloud but we will leave that for a later tutorial. Give the database any name you want and hit the "Create" button.

Now that we have a database to put our images in and make them in to targets (Vuforia automatically manages the process to make the images in to targets) we simply need to have an image of an item we want to have our VR app instantiate the sphere on top of. You can use anything around you, I used a pack of gum since that was near me. Use anything that has a semi unique packaging or look to it. The easiest way to get the image for me was to take a picture with my phone and then send it to myself on the computer so I could then upload it. Just make sure that whatever picture you take of the item has that item itself fill almost the entire picture and that it is as clear and in focus as possible. When you have the image of your target ready to go head to the next step.

You will now see that name in the Target Manger menu, select it. You can now see all the images you have as targets within that database. We do not have any yet so it is blank and we want to add a new image so we select "Add Target". You can add many types of targets but we want to have "Single Image" selected. Click the "Browse" button and find the image that we wanted to use from the previous steps.

The next step is rather tricky and I am still learning to master it myself but you want to enter in the Width of the image, this will help to scale the item when you put it in your Unity scene. I have found that entering something like 0.24 seems to work well in here and matches up pretty easily with basic Unity GameObjects. 

Last you will want to enter a name for the image. When you have done that hit the "Add" button.

Your image is now being added to this Vuforia database and you will see the Status column is listed as "Processing" or "Active". If it is processing you will need to refresh the page in a few minutes because Vuforia is building the ImageTarget from the image you uploaded. If you see "Active" you know the processing is done and your database is now readtg to be downloaded and used in your Unity app!

As a side note you will see a column called Rating. This represents on a scale of 1-5 stars how well Vuforia thinks the app will be able to recognize the ImageTarget. I have found that anything less than 4 stars is not going to work well at all, so if you see this as less than 4 stars you may want to take another picture of the item and upload it again. 
















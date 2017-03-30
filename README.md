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

<h3> Adding ImageTarget Database to your Unity Project </h3>

So now that you have your image target database setup make sure that you have the checkmark next to the image selected and hit the "Download Database" button. You will be given a list of development platforms to select from, we are going to choose Unity Editor and hit the "Download" button. This will download a .unitypackage file. Simply open this file once it is downloaded, if you also have Unity open on the project we are working on (which you should if you have been following this tutorial) then when you click the .unitypackage Vuforia databse file you will be presented with an Import Unity Package popup. Simply make sure all the items are checked and then hit the "Import" button. 

Your ImageTarget database is now in the Unity Editor. To check that this worked successfully you should go in your Unity Editor to the project panel. In there choose the folders Editor -> QCAR -> ImageTargetTextures -> "the name of the database you made". You should see a file in their with the name you have given your image in the database. Now as of right now Unity does not convert the image correctly on import so you will need to select the image and in the Unity Inspector change the "Texture Type" to "Default" and the "Texture Shape" to "2D". You will have to click away and then it will prompt you to accept the changes, when you accept you should be able to now see and preview your image.

To finish up adding this database to our Unity project we need to go back to the ARCamera, so click on that in the Hierarchy. Click the "Open Vuforia configuration" button. We need to Load the database and set it active so that Unity knows to use that database when looking for ImageTargets when our app is running. So under the "Datasets" dropdown find the checkbox with "Load" and your database name, check the box. Also make sure to check the "Activate" checkbox that pops up underneath. I dont want to go in to too much detail here but you can only have one database "Active" at any given time but you can programmatically change which database is active. For out purposes one database is all we need so we load it and set it active.

<h3> Adding an ImageTarget to your Unity scene </h3>

Now that we have our ImageTarget database all loaded and set we can add an ImageTarget prefab to our Unity scene. Go to the Vuforia -> Prefabs folder in the Projects panel. You will see multiple prefabs, drag and drop the "ImageTarget" prefab from this folder in to the Hierarchy. We now need to adjust the camera slighlty so we can see the ImageTarget GameObject, for development purposes it will be easier this way, so select the ARCamera and change its Y Position to 10 (or whatever works for you to see the ImageTarget in the Game preview window). 

Now that we can preview the ImageTarget lets add our image we had from our ImageTarget database. Select the ImageTarget in the Hierarchy and in the Inspector look for the "Image Target Behaviour" script. Set the variables to be

Type: Predefined
Database: *Name of your database*
Image Target: *Name of your target*

You should now see your image appear in the Game Preview window as well as on the ImageTarget object in the Scene view. 

The next step is to add the sphere we want to appear when we see this ImageTarget using the app and the phone camera. So with the ImageTarget selected in the Hierarchy right click it. Choose to "3D Object" and then "Sphere", this should create a sphere GameObject as a child of the ImageTarget. Adjust the sphere scale and position so that it is around the same size as the ImageTarget and hovers slightly above the ImageTarget.

That is all you need to do with editing the scene, we just need to make some changes to the Build Configuration so it will build for Android.

<h3> Build Configuration changes and testing the app! </h3>

Lets make it so that our App compiles and runs on Android devices. Go to "File" in the toolbar and select "Build Settings". Click the "Add Open Scene" button. In the "Platform" menu choose Android and then hit the "Switch Platform" button. Unity will recompile your project so just wait a minute. When that is done hit the "Player Settings" button. So one of the tricks to using Unity and building your project for Android is that you need to make sure that the "Company Name" field and the "Product Name" field match up with the "Bundle Identifier" field in the "other settings" section. 

So first off change the "Company Name" to something that makes sense to you, I just use my name so "JasonBenner" next you do not need to change the "Product Name" if you dont want to, it will just default to whatever you named your project. The last thing to do is click the "other settings" box and it will expand to show you many options. The one we want to change is the "Bundle Identifier" you will need to change this to

com.*Company Name*.*Product Name*

so in my case it is

com.JasonBenner.ARTutorialBasics

Ok so save your project now, make sure your phone is plugged in to your computer, and then back in the Build Settings window select the 
"Build and Run" button. You may be asked to save your apk file if this is the first time you are building your project so just save it with whatever name you want, I usually do "main".

Once Unity builds your app and installs the apk on your phone you it will also likely start your application up. So just wait a while for this to happen. Now that you app is running use your phone and aim the camera at the item you used in your image target. You do need to usually wait a few seconds for the camera to focus and also you may need to move the camera around a bit depending on how well your image is able to be detected but the sphere GameObject should now show up on top, hovering above, your item in the camera. 

<h3> CONGRATS ON YOUR FIRST AR APP!! </h3> 

Well I know that we didnt do anything complicated in this tutorial but just look at what you accomplished, you created a virutal object that seems to be hovering above a real object in the real world! That is pretty cool and you should feel really good about this!

There is so much more you can do however and I am sure that your brain is already thinking of all the possibilites like mine was when I created my first AR app. 

I am thinking that my next tutorial will go through the next step that I took on my AR development journey and that was to instead of instantiate a sphere GameObject with an ImageTarget I thought about instantiating text next to the object. Like maybe when you see something it will tell you about that item with a little pop-up next to the item within the real world space. Also I will add in another element that I did after that which is similar, adding a video that pops up next to the item and plays. Both of these will require some edits to the basic Vuforia scripts so we will also get in to some basic C# coding next tutorial (fun stuff I promise!)

I encourage you to continue to experiment and explore the Vuforia samples that are provided in the package that we imported. They are great starting points and learning tools, that is how I go started in Vuforia development. 













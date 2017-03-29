# UnityVuforiaARIntro

<h3> Required software and knowledge </h3>

This repository is a intro tutorial for people interested in starting to use Unity and Vuforia for AR applications.

I am going to assume that you have Unity already installed on your computer and that you have a basic level of understanding of the Unity editor and C# scripting. In this tutorial we do not do anything too complex with either the editor or scripting so dont worry if you are still relatively new.

If you do not have Unity installed go to www.unity3d.com and install it. As I write this the latest version of Unity for Windows is 5.5.1f1

Next thing that you will need is the Vuforia SDK for Unity. Go to https://developer.vuforia.com/ and register for a free account. Once you have an account and are signed in go the "Downloads" tab and choose the "SDK" tab undearneath that. You will want to "Download for Unity", as I write this the latest Vuforia version is 6.2.10.

<hr> </hr>

<h3> Basic Unity Vuforia setup </h3>

The app that we are creating is going to be very simple. It will recognize a specific image that you have given it and then will place a Unity GameObject on top of that image in the AR scene. This is the most basic AR app that you can make but it was a starting point for me and also I think that it is a great place for you to start as well because it gives you the basics of how to make a Unity Vuforia AR scene and you can just build on it from there to make complex apps.

One last thing to note, I am going to be making this app for Android. So if you have an Android phone and you have it in developer mode enabled then you can build and test this app using your phone straight from Unity.

Open up Unity and create a new 3D project, name it whatever you want. I am going to name mine "ARTutorialBasics". 

Now lets grab the Core Features samples package from the Vuforia website. Go to https://developer.vuforia.com/ click on the "Downloads" tab and choose the "Samples" tab underneath that. Look for the "Core Features" and then click "Download for Unity". This will give you a .zip file with the basic components that you will need to create this VR app. You will notice that there are a lot of really cool Core Features in the Vuforia SDK but for this very basic starter app we are only going to be concerned with "Image Targets". In later tutorials we will go through more of the Core Features and also use some of the features listed in the "Advanced Topics" samples.

Once the "Core Feature" has downloaded lets create a new folder on the desktop to hold the .zip contents. I am going to name mine VuforiaSamples but feel free to name the folder whatever you want.





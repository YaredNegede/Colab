Colab
=====

This is a project for mobile apps and services class at Georgia Tech.

It's an Android app designed to help students to collaborate with classmates easily, discuss problems together, and find study partners who are nearby. When a student logs onto this application, their classes are automatically added to their 
profile. They are able to see other students who are also using the application and are in their 
same class as well as where on campus they are located. 

How it works
=====

The application first checks whether the current user is a legitimate Georgia Tech (GT) student, by veryfing his GT credentials during login.
The credentials are verified by the CAS server (central authentication server) from Georgia Tech.
CAS doesn't have API, it does the authentication only through the browser and issues session id. 

So after user launches the app and presses login button, the apps open automatically browser with webview with CAS login page. After successful authentication, CAS issues
session id, which is returned to our app. This session id is used during
usage of the app, especially during calls to our API that requires CAS
session id. 

Once the user is authenticated, the home screen would be populated with 
related course data from the database (Screenshot 2). In the background, there're HttpPost and HttpGet requests to the RESTful API on the server side.
Currenlty these are:
* Get information about current user
* Get his courses
* Get list of other students for each class
* Post user's location to remote DB
* Get chat messages, if there are any

User can see the availability of other students (green - online, orange - away, red - offline). After selecting any of other students, the user can see a profile of other user and start chatting with him.

Screenshots
=====

![ScreenShot](https://raw.github.com/pkwiecien/Colab/master/screenshots/LoginPage.png) ![ScreenShot](https://raw.github.com/pkwiecien/Colab/master/screenshots/Pager.png)

![ScreenShot](https://raw.github.com/pkwiecien/Colab/master/screenshots/StudentInfo.png) ![ScreenShot](https://raw.github.com/pkwiecien/Colab/master/screenshots/Chat.png)

Use case:
=====

As an example of this application in use: a student is sitting in the library, trying to finish his homework assignment that is due at midnight. Time is running out and he is still stuck on 
one of the problems. He pulls out his smartphone and opens Colab where he can see that one of his classmates, Katie, is online very close and is just two minutes walking distance away. The 
student is then able to message Katie and with her help he is able to finish the assignment with clear understanding of the material.
Applications such as Facebook could arguably be used for this purpose, but social media 
sites can serve as a great distraction to students and most of the time communication is only easy 
with our “Friends” or people who we have already met. This application allows communication 
with any student in the class who decides to also utilize it even if two people are not “Friends”. 
Once the user has found a student who is also in the same class, he is able to send them a 
message in order to meet up which is made convenient by the location feature. If there happens 
to be no other students online, then the user also has the option of posting the question to the 
class forum which can be advantageous for students living/studying off campus. Students may 
also set their visibility on or off to ensure control over privacy.

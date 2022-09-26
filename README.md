# Twitter Account Checker App

## What is Twitter Account Checker? 
Twitter Account Checker app is a cross-platform mobile app using [Flutter](https://github.com/flutter/flutter) that is designed to keep track of the
twitter accounts user have been following and give a score of how these accounts might be a bot based on their profile and tweets.

## Features
- Twitter signin authentication
- Each user has seperate database
- Display all your following Twitter accounts and their BotoMeter scores in tabs
- Display all previous result from database
- Easy to use, 0 manual input (2 buttons and a scrolling list in total)

## Agile Software Design

### Design Descison / Process
1 - Decided to develop in cross-platform using flutter because of the native enviornment provided by flutter. Planned to implement an application with simple interface for user to use. For example, [Botometer](https://botometer.osome.iu.edu) requires users to manually input Twitter username 1 by 1. We can simplify by reading Twitter API to get our following ids and loop entrys into botometer API and print results. Designed UI with a similar color scheme to twitter, blue / dark blue / grey is the main color scheme here.

2 - Setup Firebase with Twitter Signin Authentication only, thus getting user's twitter uid and username after loggin in the application. Setup Cloud Firestore and create collection with the name of Firebase.instance.currentUser.uid so every user will have their unique database and reused when next login. Set up Twitter Developer Account get API keys, Bearer Tokens, Client id, Client secret to have access to Twitter API. Setup [BotoMeter-API](https://rapidapi.com/OSoMe/api/botometer-pro) via RAPID API. Downgraded our dart package of twitter API to v1.1 after realising Botometer API does not support the new released Twitter API v2.

3 - Map data from APIs into classes, lists, variables and saved the 2 most important variables: Twitter username (screenName) and Twitter uid (id_str) into Cloud Firestore for each user from GET followers/ids. Map GET statuses/user_timeline + GET statuses/user_mentions into required body for Botometer API and connect to Rapid API via HTTP POST method. Map the response.json and get the bot_Score we want. Load the botScore with the important variables into database. The app is constantly reading from the user's database and generate tabs with their info and bot Score for every following account.

### Testing and Result / Images
* The Login Home Page
* Request Authorization from Twitter
* The Main Home Screen
* The Accounts following on Twitter
* The BotoMeter Web scores on following accounts
* Firebase authentication
* Cloud Firestore Database

### Install requirements
Since the IOS xcodeproj, PODFILE and Android .gradle is too large to be submitted to Github, here is the tutorial to install the application
1 - Install flutter 
2 - run "flutter doctor -v" to see what you need to do
3 - run "flutter pub get" on these dependancies from pubspec.yaml
```cupertino_icons: ^1.0.2
  firebase_core: ^1.22.0
  firebase_auth: ^3.9.0
  cloud_firestore: ^3.4.8
  twitter_login: ^4.2.3
  http: ^0.13.5
  auto_size_text: ^3.0.0
  dart_twitter_api: ^0.5.6+1
 ```
 4 - Download the Assets and libs folder and drop into your working directory
 5 - flutter run (and hope for the best :)

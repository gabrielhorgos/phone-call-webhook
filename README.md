# Phone Call Webhook
Spring Boot app which can respond to incoming phone calls by playing callers a short message followed by a Rogers and Hammerstein song  "It Might As Well Be Spring".

# Introduction
This app is realised by using Twilio's APIs to enable communication by phone.
This means that by calling a certain number, Twilio mill make a HTTP request to the Phone Call Webhook Spring Boot app to discover what it should do - this is called a webhook.

## Twilio
Hook your app to a phone number using https://www.twilio.com/

## Ngrok
Ngrok is a tool that will allow us to make our local service (Phone Call Webhook) available on an internet-accessible URL.

# Setup steps

## Phone Call Webhook setup
### Requirements
### Java 8
https://www.oracle.com/java/technologies/javase-jdk8-downloads.html
### Maven 
http://maven.apache.org/download.cgi

### Installation
#### Clone the project
```sh 
git clone https://github.com/gabrielhorgos/phone-call-webhook.git
```

### Build and run
#### Run maven clean install 
Go to your_project_folder and run :
```sh
your_location/phone-call-webhook>mvn clean install
```
##### Run Spring Boot app :
Go to your_project_folder/target and run :
```
java -jar phone-call-webhook-0.0.1-SNAPSHOT.jar
```

Once the application has started you can call from your browser :

```sh
http://localhost:8080/call
```

and you'll get the following response :

```sh
<?xml version="1.0" encoding="UTF-8"?>
<Response>
    <Say>Hello caller number 1</Say>
    <Play>https://static.gilliard.lol/Might_As_Well_Be_Spring.mp3</Play>
</Response>
```

#### Import and run in Intellij Idea
1. Import as maven project
2. Open Run/Debug configuration
3. Add new 'Spring Boot' configuration
4. Add 'com.essential.programming.phonecallwebhook.PhoneCallWebhookApplication' to 'Main Class' input in 'Configuration' tab
5. Build and run configuration

## Ngrok setup
Install Ngrok :
1. Go to https://ngrok.com/download and donwload the archive
2. Unzip the installation to your preferred location
3. Sign up an obtain your auth token : https://dashboard.ngrok.com/auth
4. Connect your account :
    - go to your installation location
    - run command line : 
        -   ``` ngrok.exe authtoken <YOUR_AUTH_TOKEN> ``` for Windows
        -   ``` ngrok authtoken <YOR_AUTH_TOKEN> for Linux```
5. Start http tunneling :
    - go to your installation location
    - run command line : 
        -   ``` ngrok.exe http 8080 ``` for Windows
        -   ``` ngrok http 8080 ``` for Linux

6. Two URL's will be created. You can use either one, but the recommended is to use 'https'. This URL will have to be configured later in your Twilio account.


## Setting up a Twilio phone number

1. Create a Twillio account
2. Browse the https://www.twilio.com/console/phone-numbers/incoming and here you can buy a new number for your country, making sure you check the box for Voice capability.
3. After choosing a number you'll be prompted to head to the phone number management page. Here we'll select :
    - Accept Incoming : Voice Calls
    - Configure with : Webhooks, TwiML Bins, Functions, Studios, or Proxy
    - A Call Comes in : Webhook 
    - In the input type the ngrok https URL (obtained above)
    - Select HTTP POST method 
4. Save configuration



License
----


**Free Software, Hell Yeah!**
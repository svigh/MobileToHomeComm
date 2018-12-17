This project gives the ability to control devices from the mobile phone over an internet connection.

System requirements:
    1. Any Android or iOS phone with internet access
    2. Arduino board to act as home server and listen for requests

Mobile components:
    - an iPhone with internet acces

Home components:
    - Arduino mini/R3
    - Ethernet Shield
    - ESP8266 to listen on WiFi for a signal


The Home side:
    - the Arduino board will run a python script that would listen for connections on a certain port
    - once a packet is received, it needs to be decoded
    - the packet will contain information which is used to choose which device to start monitoring
    - depending of the device, a signal will be sent to activate it or start recording logging data from it
    - some devices will be able to be activated by the mobile phone, such as a webcam or audio device
    - there needs to be an authentication method (username and password):
        -encryption with py-bcrypt maybe
    - if the phone disconnects from the server, the board should close the active device if it exists
    - the connection to the home devices will be possible only if they are connected to the network:
        - as some devices might be connected to the home computer, the Arduino board needs to communicate with the computer somehow
        - a background app will run on the computer that listens for commands from the board and activate a the sent function
    

The Mobile side:
    - an app created in Swift for the iPhone which just needs to send data back home through the internet
    - the app will have a user interface with a scroll down list of logged devices on the selected home
    - selecting each device will open another screen with a button to toggle the activity of the selected device
    - for the webcam it will then open a video feed with the live view
    - the user can have only one device active on the home network to prevent security problems:
        - when the user selects a device, then, if there is already an active device on the network it will turn off the data recording from it

# RaspiCam-UV4L
Live Web Streaming on the Raspberry Pi using UV4L

# Hardware Required :-
1. Raspberry Pi B+/2 Board (Most others should work)
2. Raspberry Pi Camera

## Installing the UV4L Driver
Open the terminal and run the following commands:

` wget http://www.linux-projects.org/listing/uv4l_repo/lrkey.asc && sudo apt-key add ./lrkey.asc`

##### Add the following line to the file /etc/apt/sources.list :

` sudo nano /etc/apt/sources.list`

`deb http://www.linux-projects.org/listing/uv4l_repo/raspbian/ wheezy main`

`$ sudo apt-get update`

`$ sudo apt-get upgrade`

`$ sudo apt-get install uv4l uv4l-raspicam`

`$ sudo apt-get install uv4l-raspicam-extras`

`$ sudo apt-get install uv4l-server`

`$ sudo apt-get install uv4l-uvc`

`$ sudo apt-get install uv4l-xscreen`

`$ sudo apt-get install uv4l-mjpegstream`

`$ sudo reboot`

Source :- [Linux Projects UV4L](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=14)

## Start the Streaming Server :-

Open the terminal and run the following commands:

` $sudo pkill uv4l `(Optional)

#### Cloning this repository onto the Raspberry Pi

To install git:

    opkg install git

Then clone this repository using `git clone <git repo URL>`.


Now run the Shell Script

` ./stream_uv4l.sh `

Alternatively you can write on the Terminal directly :-

`sudo uv4l -nopreview --auto-video_nr --driver raspicam --encoding mjpeg --width 640 --height 480 --framerate 20 --server-option '--port=9090' --server-option '--max-queued-connections=30' --server-option '--max-streams=25' --server-option '--max-threads=29' `

Notes:

The --port=9090 is the local IP port. You can use any port you like.

The --max-streams=25 is the maximum simultaneous streams.

### Knowing your Raspberry Pi's Local IP Address :-

In the terminal type :

` ifconfig `

Check and write down the inet addr at eth0 for a wired connection
                and the inet addr at wlan0 for a wireless connection.
                
  
  ## View the Stream
  
  
###  To see the streaming follow the next steps:

#### 1. Open a browser

#### 2. Type your Raspberry IP followed by the external/public port (http://RaspberryIP:9090/stream)

And boom...!!!! You're done. Now you can view the Stream from your favourite Web Browser. 

Note :- Tested for Linux,Mac OSX and Windows Systems.

# Alternatives
This is one of the best of solutions and it gets the job done with very little latency. However, you may feel that Gstreamer is better for your Application. It's your choice, I personally found Gstreamer faster, however, it requires scripts running on both Server and Client Ends. I like the universaltiy of UV4L.

For more details go to my GitHub Account Page : [ShubhamCpp](https://github.com/ShubhamCpp)
Here I have explored various other technologies, these include :-

1. MJPEG using HTTP Web Sockets

2. FFMPEG using HTTP Web Sockets

3. Gstreamer (Best in my opinion)

4. UV4L and UV4L-Raspicam (Discussed here) 

I got the best experience with Gstreamer for my application, however you may feel that something else works out for you better. This will depend on the application you are developing. I'll be happy if anyone of the following help you out in some way. :)






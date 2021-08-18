# video-streaming-experimental-setup

This is an experimental video streaming framework, we can stream different YouTube videos using different Viewport sizes and store http headers whihc include requested video chunks information. 
We also use tcpdump to record the encrypted video traces and use them later to extract fetaures such as chunk sizes throughput and packets inter-arrival time. The main samle randomly a YouTube video catalog and a list of standard viewport sizes and for each experiment uses a chrome etension to setup a video player and start playing a video. 

To use this code:
1-install dependencies; pymongo, dpkt, ...

2-install a mongodbserver

4- Download the video catalog https://drive.google.com/open?id=1MTmvOuKBE85XFyYQJBrABd2K-OOcwwVi

3-Main.py: local server, samples the video ID and viewport size and store the video traces sent by the clientplayer. 

4-if you want to enforce newtork settings, use wondershaper (on linux) or linux traffic controller, set up your own netwokr conditions, make sure to change the stroing dataset in main.py, run main on one window and clientplayer on another. Dont forget to clear the enforced settings on the used interface.

5-tcpdump, if not working from whitin the clientplayer, use it manually in cmd to capture all the traffic (make sure to select the right interface) and store it in a .pcap file

6-CLientplaye.py: is the player connecting to the Youtube server and redirecting the http header infromation to the main.py. The clientplayer also calls fucntions from readpcap.py to extract usefull information from the dumped traffic of each video flow everything is then posted to main.py. The clientplayer sue a chrome extension and you need to change the ID in clientplayer.py

7-Readpcap.py: include fucntions for processing the encrypted traces, isolating video flows(using IP add) ... 

8-encrypted_traffic_analyis.py: parse the stored data, format it and clean and store it in csv files

9-chrome extension 

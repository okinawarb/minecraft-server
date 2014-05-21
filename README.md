minecraft-server
================

### [MineCraft Server](https://minecraft.net/download) for [Okinawa.rb](http://qwik.jp/okinawarb/).
### Server IP Address: `180.235.230.179`

![SS001](https://dl.dropboxusercontent.com/u/2819285/minecraft-okinawarb_001.png)
![SS002](https://dl.dropboxusercontent.com/u/2819285/minecraft-okinawarb_002.png)

__NOTE: Server logs are being broadcasted by [ScreenX TV](http://screenx.tv/minecraft):__
[![SS000](https://dl.dropboxusercontent.com/u/2819285/minecraft-okinawarb_000.png)](http://screenx.tv/minecraft)


## How to Setup MineCraft Server
- a). Increase Swap Size
- b). Install MineCraft Server

## a). Increase Swap Size
>  cf. [swapファイルを追加する](http://linuxsalad.blogspot.jp/2009/05/swap.html)

1. `cat /proc/swaps`

	> Filename		Type	Size		Used	Priority  
	> /dev/dm-1              partition	2093052	814496-1
	
2. `sudo dd if=/dev/zero of=/swap bs=2G count=5 iflag=fullblock`

	> 5+0 records in  
	> 5+0 records out  
	> 10737418240 bytes (11 GB) copied, 3079.19 s, 3.5 MB/s

3. `sudo mkswap /swap`  

	> OKINAWARB /home/yasulab% sudo mkswap /swap                                            
	> [sudo] password for yasulab:   
	> Setting up swapspace version 1, size = 10485756 KiB  
	> no label, UUID=9ac709f4-1232-4583-967a-05e1e79d3235
   
4. `sudo swapon /swap`
5. `sudo echo "/swap    swap    swap    defaults    0    0" >> /etc/sftab`
6. `cat /proc/swaps`

	> Filename		      Type		Size	  Used	Priority  
	> /dev/dm-1            partition	2093052	804008	-1  
	> /swap                file		10485756	 0	-2  

## b). Install MineCraft Server
>  cf. [#27: Okinawa.rb サーバに MineCraft を導入する](https://github.com/okinawarb/meetups/issues/27) in [okinawarb/meetups](https://github.com/okinawarb/meetups)

1. `sudo aptitude install openjdk-6-jre`
2. `which java; /usr/bin/java`
3. `mkdir ~/minecraft; cd minecraft`
4. `wget https://s3.amazonaws.com/Minecraft.Download/versions/1.7.9/minecraft_server.1.7.9.jar`
5. `java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui` #=> `/stop` to stop server.

See [UbuntuでMinecraftサーバを構築](http://blog.makkysnote.org/archives/117) for details.
   - __Note: Need to consider how to co-exist MineCraft server with [ScreenX TV](http://screenx.tv) server.__


---
layout: post
title: Keep Windows Lumia Mobile phone's WiFi Internet sharing on
date: 2015-11-09
---
I have a old Windows phone (Lumia 520). I occasionally use it to for Internet access via WiFi Internet sharing. I found that a strange feature / bug in Windows Lumia phones. If I don't use the Internet for a few minutes, the WiFi Internet sharing automatically switches off. This problem does not exist in my "Android One" phone.

To prevent Windows Lumia from automatically switching off WiFi Internet sharing, I wrote a small shell script. This shell script continuously downloads a small web page after every few seconds. This fools Windows Lumia into thinking that someone is using the WiFi Internet sharing and it does not automatically switch off.

This script is copied below without any warranty.

	#!/usr/bin/env bash
	declare -i totalBytes eachDownload i
	for ((i=1; ; ++i)) ; do
		eachDownload=$(curl.exe www.duckduckgo.com 2>/dev/null | wc -c)
		((eachDownload == 0)) && {
			echo "No internet! Unable to download at" $(date)
			sleep 10
			continue
		}
		totalBytes=$[ totalBytes + eachDownload]
		echo $[totalBytes / 1000000] "MBs downloaded in" $i "minutes to keep wifi alive."
		sleep 60
	done

Feel free to use the above script, if it helps you. If you decide to port it to windows or find some bug in it, please inform me via the "contact" link at [Care Trainings](http://caretrainings.co.in/).

# docker-my-images
All files are Docker files. They can be used to create images.

## MergeScript
The file is to create an image to run the Cloud Recording Merge Script.<br>

How to use:<br>
1.Build the image from the file<br>
```
docker build . -f MergeScript -t agora_merge_script
```
You can also pull the built image from my repo directly without buidling the image by yourself.
```
docker pull ma447689901/agora_merge_script
```
2.Run the image(Put any script parameters at the end)<br>
```
docker run --rm -v recordingpath:/home/recording agora_merge_script -f /home/recording
```

## OnPremiseRecording
The file is to create an image to run the On-Premise recording on Nodejs web server. When running the container, it will start a web server which allow you to start the on-premise recording.<br>

How to usse:<br>
1.Build the image from the file<br>
```
docker build . -f OnPremiseRecording -t agora_onpremise_recording
```
You can also pull the built image from my repo directly without buidling the image by yourself.
```
docker pull ma447689901/agora_onpremise_recording
```
2.Run the image(The web server will run on port 3000)<br>
```
docker run -p 3000:3000 agora_onpremise_recording
```

3.Call the API to start on-premise recording. Check the repo for detail<br>
https://github.com/AgoraIO/Basic-Recording/tree/master/On-Premise-Recording-Nodejs#run-restful-server-sample

## LinuxSDK
This file is to create an image to run the Agora Linux SDK C++ demo. You can run all demo commands by this image.<br>

How to use:<br>
1.Build the image from the file<br>
```
docker build . -f LinuxSDK -t agoralinuxsdk
```
You can also pull the built image from my repo directly without buidling the image by yourself.
```
docker pull ma447689901/agoralinuxsdk
```
2.Run the image(Put any script parameters at the end)<br>
```
docker run --rm -v localfilepath:/home/test_data agoralinuxsdk <command> <parameters>
```
For example, I want to push a local video file and audio file to RTC channel. You can run the following command. The test_data is the host file path directory and it will be mounted in docker container at /home/test_data. If the appid doesn't have certificate, just pass the appId to the --token arguement. If the appid has certificate, pass the token to the --token arguement and appid not required to set in this case.
```
docker run --rm -v test_data:/home/test_data agoralinuxsdk sample_send_h264_pcm --token f1bfddd2d*********3866acd1d246150 --channelId alextest --userId 12345 --videoFile /home/test_data/send_video.h264 --audioFile /home/test_data/send_audio_16k_1ch.pcm
```
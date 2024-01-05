# docker-my-images
All files are Docker files. They can be used to create images.

## MergeScript
The file is to create an image to run the Cloud Recording Merge Script.<br>

How to use:<br>
1.Build the image from the file<br>
```
docker build . -f MergeScript -t merge-image
```
You can also pull the built image from my repo directly without buidling the image by yourself.
```
docker pull ma447689901/agora_onpremise_recording
```
2.Run the image(Put any script parameters at the end)<br>
```
docker run --rm -v recordingpath:/home/recording merge-image -f /home/recording
```

## OnPremiseRecording
The file is to create an image to run the On-Premise recording on Nodejs web server. When running the container, it will start a web server which allow you to start the on-premise recording.<br>

How to usse:<br>
1.Build the image from the file<br>
```
docker build . -f OnPremiseRecording -t on-prem
```
You can also pull the built image from my repo directly without buidling the image by yourself.
```
docker pull ma447689901/agora_merge_script
```
2.Run the image(The web server will run on port 3000)<br>
```
docker run -p 3000:3000 on-prem
```

3.Call the API to start on-premise recording. Check the repo for detail<br>
https://github.com/AgoraIO/Basic-Recording/tree/master/On-Premise-Recording-Nodejs#run-restful-server-sample

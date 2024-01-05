# docker-my-images
All files are Docker files. They can be used to create images.

MergeScript
The file is to create an image to run the Cloud Recording Merge Script.

How to use:
1.Build the image from the file
docker build . -f MergeScript -t merge-image

2.Run the image(Put any script parameters at the end)
docker run --rm -v recordingpath:/home/recording merge-image -f /home/recording

OnPremiseRecording
The file is to create an image to run the On-Premise recording on Nodejs web server. When running the container, it will start a web server which allow you to start the on-premise recording.

How to usse:
1.Build the image from the file
docker build . -f OnPremiseRecording -t on-prem

2.Run the image(The web server will run on port 3000)
docker run -p 3000:3000 on-prem

3.Call the API to start on-premise recording. Check the repo for detail
https://github.com/AgoraIO/Basic-Recording/tree/master/On-Premise-Recording-Nodejs#run-restful-server-sample

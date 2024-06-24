# Real World Application

Consider a user uploading a video in youtube.

![Youtube Pub/Sub model](/modules_new/resources/PubSubExample.PNG)

1. The upload service will take the video and sends response to user once the video is uploaded and after that the user can disconnect.
2. The upload service will publish the raw mp4 video to th message queue.
3. The compress service is subscribed to Raw mp4 video and will receive raw mp4 and process it and publishes compressed video.
4. The format service is subscribed to compressed video topic and it publishes theh 480p, 1080p and 4k video.
5. The notification service is subscribed to 4k video and sends the notification in youtube.
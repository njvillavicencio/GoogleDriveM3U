# GoogleDriveM3U
This app allows you to stream your video files stored in Google Drive to VLC player, Smart TV, TV box, Roku, etc. directly from the cloud using an m3u playlist. There is no need to use Kodi or any kind of third-party software.

How to use it?

The app will pop up a dialog asking you to choose the folder into which your video files are stored. It is not necessary that your video files are all stored directly in this folder, but we recommend you not to have more than 4 levels of folders in the tree hierarchy. This is because google drive API allows us to make only a few requests within a minute, an hour or within a day, so having several nested folders limits the benefits of using this tool.

If you want to include TV logos to your playlist, it is required that these logos be stored exactly in the same folder the video files they match using exactly the same name of the video.

For instance, suppose you have a folder called "Titanic". If you have a video file named "Titanic-1080p" stored in "Titanic", then the logo file that matches this video file must be named exactly the same way, ie, "Titanic-1080p" and be stored in "Titanic".

Important: All video files and logos you want to include in this list must be shared using at least the option "On - Anyone with the link". This way your player has access to your files.

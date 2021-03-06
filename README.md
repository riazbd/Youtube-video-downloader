# Youtube video downloader
### A Youtube video dowloader in NodeJS.
#### With the ability to extract the audio using FFmpeg
---
[![Build](https://travis-ci.com/TheUncannyScrub/Youtube-video-downloader.svg?branch=master)](https://travis-ci.com/TheUncannyScrub/Youtube-video-downloader)
[![Discord Server](https://img.shields.io/badge/Discord-Link-blue.svg)](https://discord.gg/9C7aXt8)

**Basic Usage**:
The app defaults to converting it to an audio file. To download just a video add the `-v` flag.

The app does not take a standard URL as a download link. Go to the search bar in your browser and copy the part of the URL **AFTER** :`https://www.youtube.com/watch?v=` This also applies for making a list file and for downloading from a Playlist `https://www.youtube.com/playlist?list=`

#### Warning: High CPU and Network Usage when downloading large lists or playlists as Audio (20+ URL's)

##### Example inputs:
```$ node app.js list.txt -l -a ``` = Download to audio files from a list

```$ node app.js dQw4w9WgXcQ -v ``` = Download 1 Video directly to MP4

```$ node app.js PLFgquLnL59amEA53mO3KiIJRSNAzO-PRZ -a -p``` = Download to Audio directly from a Youtube Playlist
###
##### List of available Flags
```
-a = Audio download
-v = Video download
-d = Debug mode (Adds extra console output to view what the Code is doing)
-l = List Download (If you have a list of URLs to download)
-f = Download Audio without FFMPEG (Only available in conjunction with -a and will create massive mp3 files)
-p = Download from Playlist (https://www.youtube.com/playlist?list=XXXXXXX)
  
 

Combined Flag output examples:
-a & -l = Take the list and download audio
-v & -l = Take the list and download video
-a & -p = Take the playlist and download audio
-v & -p = Take the playlist and download video
-a = Audio only from Argument
-v = Video only from Argument
```

##### List File formatting:
Get the URLs from the videos you want but only the parts after `https://www.youtube.com/watch?v=`. Then seperate them by commas. 
```
jvipPYFebWc,4MCjU-Du3eI,RrutzRWXkKs
```


The JavaScript file *app.js* checks if two folders exist if not it creates them when you first run the file: *./music* and *./video* . The music folder stores the audio file and the Video folder stores the mp4 file. 
This app was a 20 minute bodge because all the other version looked unsafe or dodgey. Feel free to use this even though its buggy and dont be afraid to mess on with it. Im working to make it a more inclusive app with the ability to download entire playlists at a time.


#### Setup:
You need Node 8.11.3 or Greater and FFMPEG installed with FFMPEG also being added to the PATH Variable
Upon installing / download to zip. in the Directory that the app.js / package.json file is in run:
```
npm install
```
then you are sorted, there might be some errors please open an issue if you get one.
This app is not generally user friendly and you will need some NodeJS experience.
This App requires you to have FFMPEG.exe installed and also to be in your PATH Variable. If ffmpeg is installed but not in the path variable you can uncomment two lines of code to fix this:

```
proc.setFfmpegPath("C:/ffmpeg/bin/ffmpeg.exe");
```

All you need to do is uncomment that line of code in two places (ln 65 & ln 123 & ln 229) and then change the File path to where your FFMPEG binares were installed to.


#### Known Issues:
- FFMPEG must be installed even when the No_FFMPEG flag is set.
- Odd FileNames (This is known because I needed to escape some commonly used characters in the Title of the Video)

#### Working on:
- FFmpeg to not be required when not using it



#### Fixed*:
- FFmpeg is still required when not using ffmpeg to convert the files
- FFmpeg must be installed at `C:/ffmpeg/bin/ffmpeg.exe`
- Have an easier way to use FFmpeg when its installed
- Add A function to the app where it loads url's from a youtube playlist

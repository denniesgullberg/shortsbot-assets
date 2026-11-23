# Posting runbook (One Set Left, episodes 3-22)

Channel: @dennisshortz (UCAEYmYCv7Tj-6XZsX4QRxvA). Composio session "mill", YouTube account alias "dennisshortz".
Episode 1 is skipped permanently. Episode 2 is already live. Episodes 3-22 are made by Gemini and delivered to Google Drive.

## Delivery (Gemini)
Folder `dennisshortz-inbox` (Drive id 1YtU7JP38uV_ezNn8I8dZE547UsyEFl-7).
File names: `epN_shot1.mp4`, `epN_shot2.mp4`, `epN_shot3.mp4` (N = episode number, shots in story order).
A single full-length file `epN.mp4` is also accepted. Script for each episode: series/one-set-left-eps3-22.md.

## Titles (use exactly, then add " #Shorts #gym")
3 Rest day | 4 Texting between reps | 5 Dry towel wipe-down | 6 Working in | 7 Podcast intro
8 Pre-workout peak | 9 Form check angles | 10 Weight stack math | 11 Anabolic window | 12 Drop set to zero
13 Playlist hunting | 14 Breathing protocol | 15 Chalk ritual | 16 Mirror flex audit | 17 Unsolicited coaching
18 Wrist wrap engineering | 19 Glacial tempo | 20 Spotter briefing | 21 Macro tracking | 22 Giant superset
Title format: `One set left (<title lowercase first letter kept as above>) #Shorts #gym`, example from ep2: `One set left (lunch edition) #Shorts #gym`.

## Description (real newlines)
```
How many sets have you got left? One. Apparently.

One Set Left, episode N. Original gym comedy with fictional characters.

#Shorts #gym #gymhumor #gymetiquette #comedy #fitness #funny
```
Tags: shorts, gym, gym humor, gym etiquette, gym memes, fitness, fitness humor, comedy, funny, one set left. Category 24. privacy public.

## One posting run
1. Find the next episode: list channel videos (YOUTUBE_LIST_CHANNEL_VIDEOS, channelId UCAEYmYCv7Tj-6XZsX4QRxvA, maxResults 50) and read descriptions for "episode N". Next = lowest N in 3..22 not yet on the channel.
2. Search Google Drive by file name (title contains 'epN_shot' or 'epN.mp4', mimeType video/mp4), in the inbox folder first and then anywhere in Drive, because Gemini sometimes saves to another folder. Ignore files whose name does not start with epN. If missing, stop and report "episode N not delivered". Never skip ahead to N+1.
3. In COMPOSIO_REMOTE_WORKBENCH: GOOGLEDRIVE_DOWNLOAD_FILE per file, requests.get the s3url, `pip install imageio-ffmpeg`.
4. If there are several shots, join in order with the ffmpeg concat filter: scale+pad to 1080x1920, 30 fps, AAC 44.1 kHz audio. Check with ffprobe: vertical, audio present, duration <= 58 s. If it fails, stop and report; do not upload.
5. upload_local_file for the s3key, then YOUTUBE_MULTIPART_UPLOAD_VIDEO with privacy public, title/description/tags above.
6. Verify with YOUTUBE_GET_VIDEO_DETAILS_BATCH (status.privacyStatus public). Report the video id.
On quotaExceeded: do not retry in a loop, report it. One upload per run.

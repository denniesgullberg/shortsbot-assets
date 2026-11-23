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
1. List channel videos (YOUTUBE_LIST_CHANNEL_VIDEOS, channelId UCAEYmYCv7Tj-6XZsX4QRxvA, maxResults 50) and read descriptions for "episode N". Already posted = those N.
2. Candidates are N in 3..22 not yet posted. Pick the LOWEST candidate that is complete. Complete = the JSON `one-set-left-epN.json` exists and every file in its "shots" list exists as video/mp4 in Drive (no JSON: at least epN_shot1 and epN_shot2 and the file sizes look sane). Skip incomplete ones (they are posted later when they arrive); do not block on a missing episode.
3. Search Google Drive by file name (title contains 'epN_shot', mimeType video/mp4), inbox folder `dennisshortz-inbox` first, then anywhere in Drive. Ignore files whose name does not start with epN. If the same name exists twice, use the newest copy.
4. In COMPOSIO_REMOTE_WORKBENCH: GOOGLEDRIVE_DOWNLOAD_FILE per file, requests.get the s3url, `pip install imageio-ffmpeg`.
5. Join shots in order (shot1, shot2, ...) with the ffmpeg concat filter: scale+pad to 1080x1920, 30 fps, AAC 44.1 kHz audio. Check with ffprobe: vertical, audio present, duration <= 58 s. If it fails, stop and report; do not upload.
6. Metadata: title from the episode JSON (remove markdown backslashes like \#, keep the text, make sure it ends with " #Shorts #gym" without duplicates, max 100 chars); if no JSON use the title table. Description exactly as above with real newlines (the JSON description has escaped text, do not copy it). Tags: the list above plus the JSON tags, no duplicates. Category 24, privacy public.
7. upload_local_file for the s3key, then YOUTUBE_MULTIPART_UPLOAD_VIDEO.
8. Verify with YOUTUBE_GET_VIDEO_DETAILS_BATCH (status.privacyStatus public). Report the video id.
On quotaExceeded: do not retry in a loop, report it. One upload per run. If nothing is complete, post nothing and say which episodes are missing what.

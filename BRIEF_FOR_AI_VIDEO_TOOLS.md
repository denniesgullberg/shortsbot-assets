# One Set Left: brief for ChatGPT and Gemini

You are helping make short comedy videos for the YouTube channel @dennisshortz. Read this whole file first, then make the episode you are asked for. If something here is unclear, make a sensible choice and say what you chose.

## The series in one paragraph

One Set Left is a fixed-shot gym comedy. A deadpan lifter named Tom waits next to a machine that a lifter named Marcus is sitting on. Tom always opens with the same line: "How many sets have you got left?" Marcus always answers "One." What Marcus then does shows that "one set" means something very different. The viewer stays to see how long that one set takes.

## Characters (keep them identical in every episode)

- **Marcus**: classic gym guy in his thirties. Very muscular, wide shoulders, big arms, small waist. Short dark hair, red headband, grey tank top, black shorts with a white side stripe, white trainers. Calm, never rushed, never rude on purpose. He believes every word he says.
- **Tom**: also very muscular, slightly taller. Sandy buzz cut, tight green t-shirt, navy track pants, white towel over one shoulder, blue water bottle in one hand. Tired, deadpan. He says very little and his face does the work.
- Setting: a bright commercial gym, chest press machine, dumbbell rack, window on the left. Fictional gym. No logos or brand names anywhere.

## Technical specs

- Vertical 9:16, at least 1080x1920, MP4 (H.264), 30 fps.
- Length: 15 to 30 seconds, never over 58 seconds.
- One locked camera, medium two-shot at eye level, no camera movement. One cut is allowed for a time-skip gag.
- Spoken dialogue in English, natural and flat, exactly as written in the script.
- Burned-in captions are welcome: large white text with a dark outline, in the upper third of the frame. Keep the bottom 250 pixels clear because the YouTube interface covers it.
- Music: original or royalty-free only, upbeat gym pump style, mixed quietly under the dialogue. No real songs, no recognisable melodies from existing songs.
- If your tool only makes clips of about 8 seconds, deliver each shot as its own numbered file (for example `ep2_shot1.mp4`, `ep2_shot2.mp4`) with the shot order in the metadata file. The bot will join them.

## Rules (important)

- Fictional characters only. No real people, no celebrities, no lookalikes of real creators.
- Do not name or imitate any real creator, channel or brand in the video, the title, the description or the tags.
- No copyrighted characters, music or footage.
- Keep it clean: no swearing, no nudity, nobody gets hurt.
- The joke lands in the last 5 seconds. Do not explain it.

## Episodes

### Episode 1: Livestream (finished, for reference)
Tom: "How many sets have you got left?" Marcus: "One." Marcus turns his phone on himself and says in a bright streamer voice: "Hey guys, welcome back, today we're doing chest." Tom stares into the camera. A card reads "41 MINUTES LATER". Tom now has a long grey beard and the window shows night. Marcus is still streaming: "Okay chat, quick Q and A."

### Episode 2: Lunch
Tom: "How many sets have you got left?" Marcus: "One." Marcus opens a bag and takes out a container of rice and chicken, then a second container, then a fork he brought from home. He sits back and starts eating on the bench. Tom: "Is that your one?" Marcus, chewing: "It's a long set."

### Episode 3: Rest day
Tom: "How many sets have you got left?" Marcus: "None. It's a rest day." Tom: "Then why are you on the machine?" Marcus lies back and closes his eyes. "Recovery."

### Ideas for later episodes
Marcus checks his messages between every rep. Marcus wipes down the bench with a towel that is mostly dry. Marcus asks to work in and then does fourteen sets.

## How to hand over the finished episode

1. Name the video file `one-set-left-epN.mp4`, where N is the episode number (for example `one-set-left-ep2.mp4`).
2. Write a metadata file with the same name and a `.json` ending (`one-set-left-ep2.json`), using this template:

```json
{
  "episode": 2,
  "title": "One set left (lunch edition) #Shorts",
  "description": "How many sets have you got left? One. Apparently.\n\nOne Set Left, episode 2. Original gym comedy.\n\n#Shorts #gym #gymhumor #gymetiquette #comedy",
  "tags": ["shorts", "gym", "gym humor", "gym etiquette", "meal prep", "comedy", "one set left"],
  "shots": ["one-set-left-ep2.mp4"],
  "tool_used": "name of the tool and model you used",
  "notes": "anything the editor should know"
}
```

3. Titles: under 100 characters, end with `#Shorts`, no real creator names, no clickbait that the video does not deliver.
4. Put both files in the `inbox/` folder of the shared GitHub repository `denniesgullberg/shortsbot-assets`.
   - If you can push to GitHub, commit them to `inbox/` on the `main` branch.
   - If you cannot, give the files to the person you are working with and ask them to upload both to `inbox/` using "Add file" then "Upload files" on the repository page.
5. Tools that can only reach Google Drive (for example Gemini): save both files in the Google Drive folder `dennisshortz-inbox` (https://drive.google.com/drive/folders/1YtU7JP38uV_ezNn8I8dZE547UsyEFl-7). Use the same file names and the same metadata file as above. The bot reads this folder as well as the GitHub inbox.
6. Do not edit anything outside `inbox/` or `dennisshortz-inbox`. The bot reviews each episode, moves approved ones to `episodes/` and posts them on the schedule.

## Quality check before you hand over

- Does Tom open with exactly "How many sets have you got left?"
- Is the answer "One." (or the stated variation for that episode)?
- Do Marcus and Tom look the same as in the character descriptions?
- Is it vertical, under 58 seconds, with the bottom 250 pixels clear?
- Is the music original or royalty-free and quiet under the dialogue?
- Does the last 5 seconds deliver the joke without explaining it?

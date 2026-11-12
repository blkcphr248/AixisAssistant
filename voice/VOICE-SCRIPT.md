# Aixis voice lines to generate

Generate each line below in the Aixis voice, one file per line, named by its ID (`wake.wav`, `intro-1.wav`, and so on). Drop them in `deliverables/aixis-assistant/voice/raw/`. I cut, trim, convert to mp3 and wire them in.

Rules for the takes:
- Say only the text after the tone cue. Do not read the cue or the ID.
- One line per file. Half a second of silence at each end is fine; I trim it.
- No names. Aixis never says "Anson" in a clip, so one clip works for everyone.
- Say "Aixis" as "Axis" (the prototype already spells it "Aixis" on screen).

Already done (cut from the first recording): `intro`, `greet`, `thanks`, `bye`.

## Priority 1: spoken every session

| ID | Tone | Line | Plays when |
|---|---|---|---|
| wake | Warm, attentive | Yes? | Wake word "Hey Aixis" heard |
| hello-am | Warm, bright | Good morning. Aixis here. | Voice opens before noon |
| hello-pm | Warm | Good afternoon. Aixis here. | Voice opens 12 to 6 PM |
| hello-eve | Warm, softer | Good evening. Aixis here. | Voice opens after 6 PM |
| hello-end | Warm | What can I do for you? | After any hello |
| hello-brief | Brisk | Go ahead. | Brief mode voice open |
| bye-brief | Brisk | Okay. | Brief mode "that's all" |
| idle | Gentle | Tap the orb when you're ready to talk. | Mic idle after silence |
| listening | Calm | Go ahead, I'm listening. | Mic opens |

## Priority 2: confirmations after an action

| ID | Tone | Line | Plays when |
|---|---|---|---|
| note-saved | Warm | Got it. I saved that to your notes. | "Take a note" |
| note-saved-brief | Brisk | Noted. | Brief mode note |
| remind-set | Warm | Okay. Reminder set. | "Remind me" (time is on screen) |
| reminder-due | Clear, friendly | Quick reminder. | Reminder fires, then the text is read by browser voice |
| invite-times | Warm | I checked both calendars. Pick a time and I'll send the invite. | Meeting times shown |
| email-draft | Warm | Here's a draft. Give it a read and send it when it sounds right. | Email draft shown |
| teams-draft | Warm | Here's a Teams message. Send it as is or tweak it first. | Teams draft shown |
| files-found | Warm | I found a few files. The best match is at the top. | Files card shown |
| doc-started | Warm | I started a draft for you. Open it when you're ready. | Word or Excel card |
| nothing-found | Calm | I can find the right person, book meetings, draft messages and find files. What are you working on? | No match |
| mic-blocked | Apologetic | The microphone isn't available here, so I switched to demo voice. | Mic denied |
| done-confirm | Warm | All set. | Generic done |

## Priority 3: personality

| ID | Tone | Line | Plays when |
|---|---|---|---|
| brief-open | Confident | Here's your day. | "Brief me" |
| caught-up | Warm | You're all caught up. | Empty inbox or Teams |
| thinking | Light | Let me take a look. | Before a slow lookup |
| sorry | Apologetic | Sorry, I didn't catch that. Could you say it again? | Empty or unclear speech |
| joke-1 | Playful, dry | Why do coatings make great friends? They always have your back, and your front, and both sides. | "Tell me a joke" |
| joke-2 | Playful, dry | Why was the spray booth so calm? It had excellent humidity control. Most days. | "Tell me a joke" |

## How I wire them

1. Cut each file to `voice/<id>.mp3` (mono, 24 kHz, 30 ms fades), the same as the first four.
2. Add each line's exact text to the `CLIPS` map in `index.html`. The prototype plays a clip when the text it is about to speak matches a key.
3. Change the prototype's own wording to match the clip text wherever they differ (for example the time-of-day greeting no longer reads your next meeting).
4. Re-transcribe every clip with local Whisper and compare it to this table before I call it done.

Anything not in this table keeps using the browser voice.

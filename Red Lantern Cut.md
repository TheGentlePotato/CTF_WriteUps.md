# Red Lantern Cut — OSINT Writeup

## Challenge Information
- **Name:** Red Lantern Cut
- **Points:** 270
- **Author:** 0x4sh
- **Category:** OSINT / Media Forensics
- **Flag Format:** `0xV01D{SeriesName_SXX_EXX_MM:SS}`

---

## 💻 Methodology

### Step 1: Initial Reconnaissance (Visual Search)
The challenge provided a single frame extracted from a TV series storyline. To identify the source material, I performed a reverse image search using **Google Lens** on the provided frame.

The visual matches pinpointed the exact scene:
* **Series:** *The Punisher* (or *Marvel's The Punisher*)
* **Related Episode:** Season 1, Episode 10 (*"Virtue of the Vicious"*)

![Google Lens Verification](googleLens.png)

---

### Step 2: Locating the Video Source
With the exact season and episode identified, I navigated to **VidBox** to locate the video file for fine-grained frame matching. 

I scrubbed through the episode until the background layout, lighting, and the actor's stance perfectly matched the challenge image. 
* **Initial Timestamp Found:** 37:47

![VidBox Scene Location](Netflix.jpg)

---

### Step 3: Calibrating the Time Offset
Streaming platforms like Netflix include dynamic branding intros at the very beginning of the stream. For CTF challenges, these are typically stripped or differ from local reference media copies.

Knowing that the Netflix dynamic intro lasts exactly **6 seconds**, I subtracted this offset to find the raw video timestamp:

**37:47 - 6 seconds = 37:41**

![Exact Frame Proof](Jackpot.jpg)

---

## 🏁 Flag Submission

Following the requested format `0xV01D{SeriesName_SXX_EXX_MM:SS}`, I sanitized the series naming conventions:

* **First Try (with Publisher Prefix):** `0xV01D{Marvel'sThePunisher_S01_E10_37:41}` ❌ *Incorrect*
* **Second Try (Clean Title):** `0xV01D{ThePunisher_S01_E10_37:41}` 🟢 *Correct*

### Final Flag
```text
0xV01D{ThePunisher_S01_E10_37:41}

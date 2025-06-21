---
title: Dada Poem And Video
author: MCC
date: 2025-06-17
layout: post
---


[i zimbra](https://www.youtube.com/watch?v=qKFn66dzdz0)

i zimbra - Talking Heads

Gadji beri bimba clandridi
Lauli lonni cadori gadjam
A bim beri glassala glandride
E glassala tuffu i zimbra
Bim blassa glassala zimbra
Bim blassa glassala zimbra bim
A bim beri glassala grandrid
E glassala tuffu i zimbra
Gadji beri bimba glandridi
Lauli lonni cadora gadjam
A bim beri glassasa glandrid
E glassala tuffu i zimbra

---

Dadaist Hugo Ball's poem “Gadji beri bimba"

Gadji Beri Bimba
gadji beri bimba glandridi laula lonni cadori
gadjama gramma berida bimbala glandri galassassa laulitalomini
gadji beri bin blassa glassala laula lonni cadorsu sassala bim
gadjama tuffm i zimzalla binban gligla wowolimai bin beri ban
o katalominai rhinozerossola hopsamen laulitalomini hoooo
gadjama rhinozerossola hopsamen
bluku terullala blaulala loooo

zimzim urullala zimzim urullala zimzim zanzibar zimzalla zam
elifantolim brussala bulomen brussala bulomen tromtata
velo da bang band affalo purzamai affalo purzamai lengado tor
gadjama bimbalo glandridi glassala zingtata pimpalo ögrögöööö
viola laxato viola zimbrabim viola uli paluji malooo

tuffm im zimbrabim negramai bumbalo negramai bumbalo tuffm i zim
gadjama bimbala oo beri gadjama gaga di gadjama affalo pinx
gaga di bumbalo bumbalo gadjamen
gaga di bling blong
gaga blung

<hr style="background-color: rgb(237, 40, 5); height: 3px;">


## A. Ripping video foff Youtube using Linux

Linux provides powerful command-line tools that make this task quite straightforward.

You'll primarily need two pieces of software:

1.  **yt-dlp**: A highly capable command-line program to download videos from YouTube (and many other sites). It's a fork of the popular `youtube-dl` and is actively maintained.
2.  **FFmpeg**: A complete, cross-platform solution to record, convert and stream audio and video. You'll use this to cut the downloaded video to your desired snippet.

Here's a step-by-step procedure:

### Step 1: Install yt-dlp and FFmpeg

**For Debian/Ubuntu-based systems (like Linux Mint, Pop\!\_OS):**

```bash
sudo apt update
sudo apt install yt-dlp ffmpeg
```

If you're using a different distribution, consult your package manager's documentation or the official websites for `yt-dlp` and `FFmpeg` for installation instructions.

### Step 2: Download the YouTube video (or a portion of it)

While you *can* download the entire video and then cut it, `yt-dlp` in conjunction with `FFmpeg` can actually download *only* the specific portion you want, which is much more efficient for long videos.

You'll need the YouTube video URL and the start/end times for your 5-10 second snippet. Let's say you want a 7-second clip starting at 1 minute and 30 seconds into the video.

**Command to download a specific section:**

```bash
yt-dlp --external-downloader ffmpeg --external-downloader-args "ffmpeg_i:-ss 00:01:30 -to 00:01:37" -f bestvideo+bestaudio --merge-output-format mp4 "YOUR_YOUTUBE_VIDEO_URL" -o "output_clip.mp4"
```

**Let's break down this command:**

  * `yt-dlp`: Calls the `yt-dlp` program.
  * `--external-downloader ffmpeg`: Tells `yt-dlp` to use `ffmpeg` for the download process. This is crucial for cutting on the fly.
  * `--external-downloader-args "ffmpeg_i:-ss 00:01:30 -to 00:01:37"`: These are arguments passed directly to `ffmpeg`.
      * `-ss 00:01:30`: Specifies the **start time** (HH:MM:SS format). In this example, it starts at 1 minute and 30 seconds.
      * `-to 00:01:37`: Specifies the **end time** (HH:MM:SS format). This will make your clip 7 seconds long (00:01:37 - 00:01:30 = 00:00:07).
      * **Important Note on `-ss` placement**: When `-ss` is placed *before* the input file (`-i`) (as shown here with `ffmpeg_i:`), FFmpeg performs a "fast seek," which is quicker but might not be frame-accurate at the beginning. If absolute frame accuracy is critical for your starting point, you might need to download a slightly larger segment and then perform a second `ffmpeg` cut (see "Alternative: Cut an already downloaded video" below). However, for a 5-10 second YouTube snippet, this method is usually perfectly fine.
  * `-f bestvideo+bestaudio`: Downloads the best available video and audio quality.
  * `--merge-output-format mp4`: Ensures that if the video and audio streams are separate, they are merged into a single MP4 file.
  * `"YOUR_YOUTUBE_VIDEO_URL"`: **Replace this with the actual URL of the YouTube video.** Make sure to enclose it in double quotes.
  * `-o "output_clip.mp4"`: Specifies the output filename for your snippet. You can change `output_clip.mp4` to whatever you like.

**Example usage:**

The YouTube video URL is `https://www.youtube.com/watch?v=39vX3u-9Gt0` and you want a 10-second clip starting at 0:00.

```bash
yt-dlp --external-downloader ffmpeg --external-downloader-args "ffmpeg_i:-ss 00:00:00 -to 00:00:10" -f bestvideo+bestaudio --merge-output-format mp4 "https://www.youtube.com/watch?v=39vX3u-9Gt0" -o "my_10_second_snippet.mp4"
```

### Alternative: Cut an already downloaded video

If you already have the full video downloaded (e.g., as `full_video.mp4`), you can use `ffmpeg` directly to cut a snippet:

```bash
ffmpeg -ss 00:01:30 -i "full_video.mp4" -to 00:01:37 -c copy "output_clip.mp4"
```

**Explanation of this command:**

  * `ffmpeg`: Calls the `ffmpeg` program.
  * `-ss 00:01:30`: Specifies the **start time**.
  * `-i "full_video.mp4"`: Specifies the **input file**.
  * `-to 00:01:37`: Specifies the **end time**.
  * `-c copy`: This is important\! It tells `ffmpeg` to directly copy the video and audio streams without re-encoding them. This makes the process incredibly fast and avoids any loss of quality.
  * `"output_clip.mp4"`: The name of your output snippet file.

**Important Considerations for `-c copy`:**

When using `-c copy`, `ffmpeg` can only cut at "keyframes" (also known as I-frames). This means your cut might be slightly off from your exact specified time, usually to the nearest preceding keyframe. For a 5-10 second clip, this minor inaccuracy is usually acceptable.

If you need *frame-accurate* cuts, you would omit `-c copy` (which forces re-encoding), but this will take significantly longer and might result in a slight quality loss due to re-compression. For most snippets, `-c copy` is preferred.

Choose the method that best suits your needs\! The `yt-dlp` combined with `ffmpeg` method is generally more efficient for directly extracting snippets from YouTube.

<hr style="background-color: rgb(237, 40, 5); height: 3px;">

## B. How to make pcitures into charcoal srawings with GIMP.


### Method 1: Simple Pencil Sketch Effect

This method is quick and produces a clean line drawing effect.

1.  **Open your image in GIMP:**
    * Go to `File > Open...` and select your iPhone photo.

2.  **Duplicate the Background Layer:**
    * choose `Duplicate Layer`. You should now have two identical layers.

3.  **Desaturate the Duplicate Layer:**
    * Select the **top** (duplicate) layer.
    * Go to `Colors > Desaturate > Desaturate...`
    * use default "Luminosity" mode, Click `OK`.

4.  **Invert Colors of the Desaturated Layer:**
    * With the top layer still selected, go to `Colors > Invert`. Your image will now look like a photo negative.

5.  **Change Layer Mode to "Dodge":**
    * In the Layers panel, with the top layer selected, change the **Mode** dropdown from "Normal" to `Dodge`. Your image will likely turn completely white at this point – don't worry, that's expected!

6.  **Apply Gaussian Blur:**
    * Go to `Filters > Blur > Gaussian Blur...`
    * A dialog box will appear. You'll need to adjust the "Radius" for both X and Y. Start with a small value, like `5` to `10` pixels, and slowly increase it. As you increase the radius, you'll start to see the sketch lines appear.
    * The exact value depends on your image resolution and desired effect. Keep increasing it until you get a good balance of lines and detail. Click `OK` when you're happy.

7.  **Adjust Levels for Contrast (Optional but Recommended):**
    * To fine-tune the sketch's darkness and contrast, go to `Colors > Levels...`
    * In the "Input Levels" section, you'll see three triangles (black, grey, white).
        * Drag the **black triangle** (left) slightly to the right to make the darker lines more prominent.
        * Drag the **white triangle** (right) slightly to the left to brighten the lighter areas and make them more like white paper.
        * Experiment with the **grey triangle** (middle) to adjust the overall mid-tones.
    * Click `OK`.

This should give you a good pencil sketch effect!

### Method 2: More Artistic Pencil/Charcoal Look (Using `Value Propagate` or `Sobel`)

This method can give a more textured or "drawn" feel, sometimes leaning towards charcoal.

**A) Using Value Propagate (often results in a softer sketch):**

Follow steps 1-5 from Method 1 (Open, Duplicate, Desaturate, Invert, Change to Dodge). Then, instead of Gaussian Blur, do this:

6.  **Apply Value Propagate:**
    * Go to `Filters > Distorts > Value Propagate...`
    * Select the `More black (smaller value)` radio button.
    * Click `OK`.
    * **Repeat this filter (Ctrl+F) two or three more times** until you get a good sketch effect. Each time you apply it, the lines will become more defined.

7.  **Adjust Levels for Contrast (Optional):**
    * Same as Step 7 in Method 1 (`Colors > Levels...`).

**B) Using Edge Detect (can give sharper, more defined lines):**

1.  **Open your image in GIMP.**

2.  **Duplicate the Background Layer:**
    * Right-click on your "Background" layer and choose `Duplicate Layer`.

3.  **Desaturate the Duplicate Layer:**
    * Select the **top** (duplicate) layer.
    * Go to `Colors > Desaturate > Desaturate...` and click `OK`.

4.  **Apply an Edge Detection Filter:**
    * Go to `Filters > Edge-Detect > Sobel` (or `Neon`, `Edge`, etc. - experiment!).
    * For **Sobel**, you'll get a grayscale image with edges highlighted. You might want to tick "Wrap" or "Black background" depending on your preference. Click `OK`.
    * For **Neon**, set Intensity to `0` and Radius to around `5`. Then `Colors > Invert` that layer.

5.  **Adjust Levels on the Edge Layer (Crucial for a clean sketch):**
    * With your edge-detected layer selected, go to `Colors > Levels...`
    * Drag the **black triangle** (left) significantly to the right to remove faint noise and make the background truly white.
    * Drag the **white triangle** (right) slightly to the left to darken the lines.
    * Click `OK`.

6.  **Change Layer Mode to "Multiply":**
    * In the Layers panel, change the **Mode** of the edge-detected layer to `Multiply`. This will blend the lines with your original (or a white) background.

7.  **Add a New White Layer (Optional but Recommended):**
    * Go to `Layer > New Layer...` and choose `White` as the fill.
    * Drag this new white layer **below** your edge-detected layer but **above** your original background image. This ensures a clean white "paper" background for your drawing. You can even hide your original background layer if you just want the sketch.

8.  **Fine-tune Opacity:**
    * You can adjust the **Opacity** of the edge-detected layer in the Layers panel to make the lines lighter or darker.

### Charcoal Specific Touches:

To make it look more like charcoal, which often has a grainier, softer, and sometimes smudged appearance, you can add these steps after any of the above methods:

* **Add Noise:**
    * On your sketch layer, go to `Filters > Noise > HSV Noise...`
    * Adjust the "Holdness" and "Hue", "Saturation", "Value" sliders to introduce a subtle grain that mimics charcoal texture. Keep it low to avoid making it look digital.

* **Slight Gaussian Blur (again):**
    * A very subtle Gaussian blur (`Filters > Blur > Gaussian Blur...` with a radius of `0.5` to `1.5`) can soften the lines slightly, making them less sharp and more smudged like charcoal.

* **Desaturate to Grayscale (if not already):**
    * Ensure your final image is completely grayscale by going to `Image > Mode > Grayscale`.

* **Optional: Add a Paper Texture:**
    * Find a subtle paper texture image online (e.g., a scanned sheet of drawing paper).
    * `File > Open as Layers...` and select your paper texture.
    * Place this paper texture layer **below** your sketch layer but **above** any solid white background layer.
    * Change the blending mode of the paper texture layer (e.g., `Overlay`, `Soft Light`, or `Multiply`) and adjust its opacity to subtly show through your drawing, giving it a more authentic feel.

Remember that experimentation is key in GIMP! Play around with the filter settings, layer modes, and opacity until you achieve the exact pencil or charcoal look you desire. Every photo will react differently, so be prepared to make minor adjustments.


<hr style="background-color: rgb(237, 40, 5); height: 3px;">


## C. Scratch Video


That's a great idea for a Scratch project\! While Scratch isn't primarily a video editing tool, you can absolutely create a slideshow-style "video" with pictures and a soundtrack. It will feel much like a stop-motion animation or a sequence of scenes.

Here's a step-by-step guide on how to do this using Scratch.mit.edu:

### Phase 1: Prepare Your iPhone Photos

1.  **Transfer Photos to Your Computer:** Get the pictures from your iPhone onto your computer. You can use:
      * **USB Cable:**
      * **Cloud Services:** Dropbox
      * **Email/Airdrop:**

2.  **Crop and Resize (Recommended):**
      * **Scratch Stage Size:** The Scratch stage is **480 pixels wide by 360 pixels high**.
      - If your photos are larger, they will take longer to load and might look pixelated when scaled down.
      * **Recommended:** Briefly resize your photos to be close to or slightly larger than 480x360 pixels. You can use any basic image editor (like Paint on Windows, Preview on Mac, or GIMP/Pinta on Linux). You can also crop them to a 4:3 aspect ratio (like 480x360) if you want them to perfectly fill the screen without distortion or black bars.
      * **Save as JPG or PNG:**

### Phase 2: Prepare Your Soundtrack

1.  **Obtain Your Audio File:** Get the music track
      * **Legal Considerations:** Be mindful of copyright
      * **Supported Formats:** Scratch supports `.wav` and `.mp3` files.
2.  **Trim/Edit (Optional):** If your soundtrack is too long, you might want to trim it to the desired length using an audio editor (like **Audacity**, a free and open-source option).

### Phase 3: Create Your Project in Scratch

1.  **Create a New Project:**

      * Go to [scratch.mit.edu](http://scratch.mit.edu/).
      * Click `Create` at the top.

2.  **Upload Your Photos as Sprites:**

      * **Delete the Cat Sprite:** Right-click on the default "Sprite1" (the cat) in the Sprite list below the stage and choose `delete`.

      * **Upload Each Photo:**
          * Hover over the `Choose a Sprite` button (the cat icon with a `+` sign) in the bottom-right of the Sprite list.
          * Click `Upload Sprite` (the arrow pointing up from a box).
          * Navigate to where you saved your first iPhone photo, select it, and click `Open`.
          * Repeat this for *each* photo you want to use in your video.
      * **Organize/Rename Sprites (Recommended):** To keep things organized, click on each sprite in the Sprite list and change its name (e.g., "Photo1", "Photo2") in the 'Sprite' information area above the code blocks.

3.  **Position Your Photos (Sprites):**

      * For each photo sprite, click on it in the Sprite list.
      * In the Code area, drag out a `go to x: (0) y: (0)` block from the **Motion** category. This will center each image on the stage.
      * If your photos are larger than the stage, you can use the `set size to (%)` block (from **Looks**) and adjust the percentage (e.g., `80%`, `50%`) until it fits nicely. You might need to do this for each photo if they have different original sizes.

4.  **Upload Your Soundtrack:**

      * Go to the `Sounds` tab in the middle panel (next to `Code` and `Costumes`).
      * Click the `Upload Sound` button (the speaker icon with an arrow).
      * Select your soundtrack file and click `Open`.
      * You can trim the sound directly in Scratch if needed by clicking on it in the sound editor.

5.  **Code the Sequence (Main Script on a New Sprite or Stage):**

      * **Option A (Recommended): Create a dedicated "Controller" Sprite:** This keeps your stage clean.

          * Click `Choose a Sprite` \> `Paint`. Don't draw anything, just make an empty sprite. Rename it "Controller" or "Director."
          * Click on this "Controller" sprite in the Sprite list.

      * **Option B: Code on the Stage:** Click on the "Stage" thumbnail in the bottom-left of the Sprite list.

      * **Add "When Green Flag Clicked":** Drag out a `when green flag clicked` block from the **Events** category.

      * **Start the Music:**

          * From the **Sound** category, drag out a `start sound [your_sound_name]` block and select your uploaded soundtrack. (Using `start sound` allows the script to continue running; `play sound until done` would pause it.)

      * **Control Photo Visibility and Timing:**

          * From the **Looks** category, drag out `hide` blocks for *all* your photo sprites. Place these at the very beginning of your script, right after `when green flag clicked`. This ensures only one photo is visible at a time.
          * Now, build your sequence:
              * `show` (for Photo1)
              * `go to x: (0) y: (0)` (for Photo1, if you didn't do it per-sprite, or if you want to explicitly reset position)
              * `wait (seconds)` (from **Control** category - this is how long Photo1 stays on screen)
              * `hide` (for Photo1)
              * `show` (for Photo2)
              * `go to x: (0) y: (0)` (for Photo2)
              * `wait (seconds)` (for Photo2)
              * `hide` (for Photo2)
              * ...and so on for all your photos.

      * **Example Script Structure (on your Controller Sprite):**

    <!-- end list -->

    ```scratch
    when green flag clicked
    hide (Photo1)    // Initial hides for all photos
    hide (Photo2)
    hide (Photo3)
    // ... and so on for all your photos

    start sound [MyAwesomeSoundtrack] // Make sure you select your actual sound

    // Photo 1
    show (Photo1)
    go to x: (0) y: (0)
    wait (5) seconds // Show Photo1 for 5 seconds
    hide (Photo1)

    // Photo 2
    show (Photo2)
    go to x: (0) y: (0)
    wait (7) seconds // Show Photo2 for 7 seconds
    hide (Photo2)

    // Photo 3
    show (Photo3)
    go to x: (0) y: (0)
    wait (6) seconds // Show Photo3 for 6 seconds
    hide (Photo3)

    // ... continue for all your photos
    // At the very end, you might want to stop the sound if it's longer than your total photo sequence
    stop all sounds
    ```

6.  **Test Your Project:**

      * Click the Green Flag to run your project.
      * Watch and listen to see if the timing is correct. Adjust the `wait` times as needed.
      * If you need precise timing, you can listen to your soundtrack and note down the exact second marks where you want each picture to change.

7.  **Share Your Project (Optional):**

      * If you're happy with your "video," click the `Share` button (top right of the Scratch editor).
      * Add instructions and notes about your project.

### Tips for a Better "Video":

  * **Pacing:** Vary the `wait` times based on the content of the photo and the rhythm of your music.
  * **Transitions (Advanced):** You can create simple transitions by using the `change [color] effect by (25)` block (from **Looks**) and then `clear graphic effects`. Or, use a `glide` block for a subtle movement effect between photos. However, for a simple slideshow, `hide` and `show` is perfectly fine.
  * **Narrated Voiceover:** If you want to add your voice, you can record sounds directly in Scratch (in the `Sounds` tab, click `Record`). Then, intersperse `play sound [your_narration]` blocks in your script.
  * **Sprite Ordering:** Ensure your photo sprites are *above* any background you might add.
  * **Saving:** Scratch saves your project automatically as you work, but it's good practice to occasionally check that it's saving (look for "Project saved" in the top bar).

This method allows you to precisely control the order and timing of your iPhone photos synced to your chosen soundtrack, effectively creating your own Scratch video movie\!

<hr style="background-color: rgb(237, 40, 5); height: 3px;">
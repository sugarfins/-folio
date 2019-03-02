---
layout: post
title: Learning Basic And Advanced Karaoke Effects In Aegisub
description: 
img: /img/aegisub_thumb.png
---

## What and Why?

As my final project for my *Multilingual DTP and A/V Localization* course, I decided to learn how to create karaoke text effects in Aegisub, a popular open source subtitling program. I applied the skills I learned to the music video for *Zenzenzense* by *RADWIMPS*.

### Why karaoke?

I had previously worked as a translator and subtitler(timing/QA) for Chinese TV dramas, so I had used Aegisub before. However, I had mostly used the program for timing subtitles, thus I had only barely scratched the surface on Aegisub’s various features. Additionally, going karaoke is one of my favorite hobbies (although I prefer the sing-inside-a-private-room Asian style of karaoke over the go-to-a-bar Western style of karaoke) and I felt it would be great if I could create my own karaoke videos for songs that are not commonly available at commercial locations. Finally, because of having previous experience with Aegisub, I wanted to challenge myself and get out of my comfort zone with the application.

## Preparation

### Tools

* Aegisub, a subtitling program
* Youtube and video ripping sites to download a copy of the music video
  * the music video used: [Zenzenzense by Radwimps](https://www.youtube.com/watch?v=PDSkFeMVNFs)
* FFMPEG (via the command prompt) in order to hardsub my subtitle file
 
### Unexpected Challenges

Right at the beginning of the project, I ran into a slight problem. A site I usually used to rip video or audio recognized that it was a music video and wouldn’t proceed with the download, thus I had to go through a number of different sites to find a site that would allow both high quality video download and audio ripping.
## The Process

### Learning Aegisub’s style code

Previously, I had only worked with plain SRT files when doing subtitles, and any effects were added after my step in QA. Thus, one of the first things I taught myself was how to read the styling code in Aegisub. This mostly consisted of copying and pasting some styling code from other subtitle files I had and tinkering with the code. Later on, I learned how to implement a set style template so I would not need to write the style code in line by line, but working with the code initially acclimated me to how code in Aegisub was written.
One particular aspect I had to look up to implement was how to turn text vertical, but in a way that could be read down, not sideways. Interestingly, this is easily done in the styling code by adding a \{\\fn@\} to the beginning of the line. This allowed me to put my Japanese text down the right-hand side of the screen.

<div class="img_row">
  <img class="col three" src="/img/aegisub_01.png">
</div>
<div class = "col three caption">Here you can see some examples of the styling code in Aegisub, including font-type, size, border color, and position</div>

### Learning Aegisub’s karaoke function

In my experience, the majority of people who use Aegisub used it for subtitling Asian TV shows, whether they be live action dramas or Japanese animation. These shows typically have both an opening and ending song, and thus there was a large market for the ability to code in karaoke effects. Thankfully, Aegisub has a karaoke function button built right into their application, which makes simple karaoke effects very simple to implement.


<div class="img_row">
  <img class="col three" src="/img/aegisub_02.png">
</div>

Once you have selected the karaoke function button for a line, you can easily split up the text as you like, whether by syllables, characters, or words: Doing so will also create corresponding lines in the waveform, which you can listen to and move to correspond correctly with your sectioned text.

<div class="img_row">
  <img class="col three" src="/img/aegisub_03.png">
</div>

<div class="img_row">
  <img class="col three" src="/img/aegisub_04.png">
</div>

Once the text and corresponding audio is sectioned to your liking, simply click the checkmark and Aegisub will insert the necessary code to implement karaoke effects into the line:

<div class="img_row">
  <img class="col three" src="/img/aegisub_05.png">
</div>
<div class="col three caption">Cool, right? And very simple to use
</div>

### Advanced Karaoke Effects

If you wanted to implement other more complicated and visually interesting karaoke effects, this took a bit more work. The more intricate karaoke effects required knowledge of a programming language called Lua. For the amount of time I had, I did not learn how to write Lua code, but was able to implement it in my video using other people’s templates as a guide.


<div class="img_row">
  <img class="col three" src="/img/aegisub_06.png">
</div>

What you see highlighted at the top of the subtitle file is some lua code pasted from a karaoke effects template. Additionally, multiple styles can exist in a single file, thus I was able to apply the code to only the romanized Japanese lyrics and implement a different karaoke style for the Japanese text. When implementing intricate karaoke styles, you end up with many more lines of code at the bottom of your file, as seen here:


<div class="img_row">
  <img class="col three" src="/img/aegisub_07.png">
</div>

Certainly, this can seem daunting, but the implementation of styles is fairly straightforward.

## Finalization
 
### Unexpected challenges

Once I finished my subtitle file, I ran into an unexpected problem. Handbrake, a simple program we had been using during the course to burn the subtitle files into a video, did not support .ASS files, only .SRT files. Thus, I went through trying about 5 different programs and tricks to find another suitable program to burn my subtitle file into the video. After 3 hours and many unsatisfactory video files later, I ended up implementing FFMPEG to burn my video file through the command prompt (since Handbrake is really just a nice UI for FFMPEG).

<div class="img_row">
  <img class="col three" src="/img/aegisub_08.png">
</div>

### The Final Product

For the purposes of the project, my aim was to teach myself how to utilize more features of Aegisub and implement them successfully in a span of about 3 weeks, thus I did not subtitle and implement karaoke effects to the entire music video. Below is about 30 seconds of what I did implement.

<iframe width="560" height="315" src="https://www.youtube.com/embed/kBSrSv8vAik" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Final Thoughts

Overall, I had a lot of fun learning something new for this project, and am pretty happy with the final product. Obviously there are still flaws in the final product (there’s a very obvious kerning issue in the bottom text, which I would need to look into the lua code to debug), and I wish I had a bit more time to learn how to write Lua code. If I have time over the summer, I would like to implement karaoke effects through the entire video and figure out the issue with the kerning. This was definitely a fun learning experience!


# Music Player

## Overview
This project uses the Tiva C EK-TM4C123GXL board to build a device that plays retro video game music.  The music data comes from MIDI files, and is converted to an optimized format that is downloaded to the Tiva's Flash memory from the PC's serial port.  Up to 224Kib of song data can be downloaded (about 8 to 12 songs).  The firmware uses FreeRTOS, and is an example of a soft real-time system.

The buttons on the Tiva are used to cycle to the next and previous songs in the song list, and the blue button on the board toggles between Play and Stop.  An LCD displays information about the current song, such as its name, song index, track count, size, and length.  Each second, a time marker is incremented as the song plays.  

To produce the musical sounds, the Tiva's PWM channels are used to generate square waves at the audio frequencies of the musical notes.  The square waves are summed together and amplified by an LM386.  The player board supports up to four monophonic, instrument tracks, one of which can be used as a percussion track.  The percussion track generates a sound using white noise that simulates a closed hi-hat.

The firmware was designed as a state machine with a total of six states, five events, and four actions.  Zero or more actions are invoked when an event causes a transition from one state to another.   The main program is implemented by two interrupt service routines (ISRs) and eight FreeRTOS tasks.  The tasks can be in a running or blocked state at any given time.  The tasks and ISRs synchronize by giving/taking binary semaphores.   

This project builds on the work from Experiments 14-16, as well as Experiments 6 & 13.

[![](https://i.ytimg.com/vi/1OvchymIkCs/default.jpg)](https://youtu.be/1OvchymIkCs)<br>
[Watch the video](https://youtu.be/1OvchymIkCs)

## Music Samples

These mp3s were created by connecting the speaker terminal from the music player board to the mic input of the PC and recording the accompanying song (MIDI) file.

[Batman Returns - Stage 1](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Batman2-Stage1.mp3)&nbsp;*Sequenced by Johnnyz*<br>
[Castlevania 3 - Stage 1 Beginning](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/JILost_-_Famicom_-_Akumajo_Densetsu_-_Beginning.mp3)&nbsp;*Sequenced by JILost*<br>
[Golvellius - Title Screen](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Golvellius-Title.mp3)&nbsp;*Sequenced by Johnnyz*<br>
[Lemmings - Level 11 Ronda Alla Turca](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Lemmings-Level11.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[R. C. Grand Prix - Main Theme](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/RCGrandPrix.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[Renegade - Mission 1 Inside Train](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Reneg-Inside.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[Sonic the Hedgehog - Bonus Stage](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Sonic_Bonus.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[Sonic the Hedgehog 2 - Scrambled Egg Zone](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Sonic2_ScrambledEgg.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[Sonic the Hedgehog 2 - Green Hills Zone](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Sonic2_GreenHills.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br> 
[Sonic Chaos - Sleeping Egg Zone](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/SonicChaos-SleepingEgg.mp3)&nbsp;*Sequenced by Joo *Johnnyz* Buaes*<br>
[Super Mario Bros. Theme](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Smbtheme.mp3)&nbsp;*Sequenced by PJ Barnes*<br>
[Tetris - Music A](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Tet_Music_A_NES-KM-GS.mp3)&nbsp;*Sequenced by King Meteor*<br>
[Vs. Excitebike - Track 3](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/VsExcitebike3.mp3)&nbsp;*Sequenced by Chow*<br>
[Wizardry II: The Legacy of Llylgamyn - Title Theme](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Wizardry_II_Opening_Theme.mp3)&nbsp;*Sequenced by Yatorl Ogalbana*<br>
[Wonder Boy in Monster World - Shore](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/WB5-Shore.mp3)&nbsp;*Sequenced by Johnnyz*<br>
[Zelda II: The Adventure of Link](https://raw.githubusercontent.com/jspicer-ltu/Tiva-C-MusicPlayer/master/samples/Zelda2ov.mp3)&nbsp;*Sequenced by JILost*<br>


Video game MIDI files were downloaded from:<p>
[![](http://www.vgmusic.com/images/banners/lillogo.jpg)](http://www.vgmusic.com)<br>

This project uses the Midifile library from https://midifile.sapp.org/ to parse the MIDI files.

## Images

### Music Player
![MusicPlayer](picture1.png)
![MusicPlayer](picture2.png)

### Downloader Screen
![DownloaderScreen](DownloaderScreen.png)

### Circuit Diagram
![CircuitDiagram](MusicPlayer-circuit.png)

### State Diagram
![StateDiagram](StateDiagram.png)

### Task Diagram
![TaskDiagram](TaskDiagram.png)

### Track Task Flowchart
![TrackTaskFlow](TrackTaskFlow.png)

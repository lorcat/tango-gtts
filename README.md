# tango-gtts (aka P022SoundReporter)
Simple tango server for playing sound from text input.

The main purpose to notify an operating user of macro steps or failures.

Uses Google Text-to-Speech interface to download a file if a matching mp3 is not found locally.
Should be working on both - windows and linux.

## Properties of Tango server
- __cmdplay__
    
    Command used to play sound - json array as a string.
For example: 
_["/usr/bin/mpg321"]_ or
_["/usr/bin/vlc", "--intf=dummy"]_

## Attributes
- __Status__

    Displays info of the current state of program - which files processed, etc.

## Commands
- __Speak__

    Adds a text to a processing queue. If an mp3 file found which matches the text, it will be played. 
Otherwise, the server performs an attempt to use google text to speech and saves the resulting mp3 file to be played later.
The processing queue is triggered by a separate thread which may combine several speech requests into a single playlist
if the sound playing program (e.g. vlc supports it - so far only vlc is considered as playlist compatible in the code).

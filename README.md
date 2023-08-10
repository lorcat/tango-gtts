# tango-gtts (aka P022SoundReporter)
Simple tango server (python) for playing sound from text input.

The main purpose to notify an operating user of macro steps or failures.

Uses Google Text-to-Speech interface to download a file if a matching mp3 is not found locally.
Should be working on both - windows and linux.

In order to ensure the correct operation of the Google Text-to-Speech, please make sure to run code with correctly set `GOOGLE_APPLICATION_CREDENTIALS` environment variable.

One can also add a custom file into the voice directory, e.g. would you like a `Bankai!` for a beam dump?

The file was made with `pogo` of `Tango Controls`, the modification of the server is possible and encouraged.

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
if the sound playing program supports it (e.g. vlc  - so far only vlc is considered as playlist compatible in the code).

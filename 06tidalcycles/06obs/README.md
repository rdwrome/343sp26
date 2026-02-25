# recording your sessions
## Virtual Audio Interfaces
- [BlackHole](https://existential.audio/blackhole/)
  - uncomplicated, unpowerful
  - Download 16ch
- [JACK](https://jackaudio.org/)
  - complicated, powerful

## miniTidalStrudel Audio > BlackHole > DAW or OBS
- ORDER OF OPERATIONS CRITICAL!
- **Audio MIDI Setup**
  - [(Create Multi-Output Device)](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)
  - Input: BlackHole 16ch
  - Output: Multi-Output Device
    - Your MONITOR source (external headphones, etc.) Use box checked!
- **miniTidalStrudel IN CHROME**
  - Settings
  - Audio Output Device
  - Select: BlackHole 16ch
- **DAW**
  - Input: BlackHole 16ch
  - Output: Multi-Output Device	
- **OBS**
  - Main Window: Add Source to Scene
    - Audio Input Capture
      - BlackHole 16 ch

## TidalCycles/SuperCollider Audio > BlackHole > OBS
- ORDER OF OPERATIONS CRITICAL!
- **Audio MIDI Setup**
  - [(Create Multi-Output Device)](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)
  - Input: BlackHole 16ch
  - Output: Multi-Output Device
    - BlackHole 16ch Use box checked!
    - Your MONITOR source (external headphones, etc.) Use box checked!
- **SuperCollider**
  - Input: N/A
  - Output: BlackHole 16ch
  - If you need to change it run this then reboot server:
`Server.default.options.outDevice_("BlackHole 16ch");`

- **OBS**
  - Main Window: Add Source to Scene
    - Audio Input Capture
      - BlackHole 16 ch
	  

## [obs 101](https://obsproject.com/)
- scenes
- sources
	- macOS screen capture
	- create new
	- method
	- display
	- rightclick>transform
- "audio"
	- OBS Studio>Preferences
		- Global Audio Device: Desktop Audio: BlackHold 16ch
		- Advanced: Monitoring Device: Your MONITOR source
	- Audio Mixer>"cog" icon
		- Monitor and Output
- streaming vs studio
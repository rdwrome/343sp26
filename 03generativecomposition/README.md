# recording your sessions
## Virtual Audio Interfaces
- [BlackHole](https://existential.audio/blackhole/)
  - uncomplicated, unpowerful
  - Download 16ch
- JACK
  - complicated, powerful

## miniTidalStrudel Audio > BlackHole > DAW or OBS
- ORDER OF OPERATIONS CRITICAL!
- **Audio MIDI Setup**
  - [(Create Multi-Output Device)](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)
  - Input: BlackHole 16ch
  - Output: Multi-Output Device
    - BlackHole 16ch Use box checked!
    - Your MONITOR source (external headphones, etc.) Use box checked!
- **miniTidalStrudel**
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

## [obs 101](https://obsproject.com/)
- scenes
- sources
- "audio"
- streaming vs studio

## [estuary](https://estuary.mcmaster.ca/)

### mini-tidal notation comparison
```
// tidal cycles
d1 $ stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  s "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  s "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  s "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] "
]

// estuary
stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  s "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  s "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  s "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] "
]

// strudel
stack(
  "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] ",
).s()

```
## sample transformations

- loop at

`samples({ rhodes: 'https://cdn.freesound.org/previews/132/132051_316502-lq.mp3' })
s("rhodes").loopAt(2)`

- begin

`samples({ rave: 'rave/AREUREADY.wav' }, 'github:tidalcycles/dirt-samples')
s("rave").begin("<0 .25 .5 .75>").fast(2)`

## sophisticated pattern transformations

- degradeBy

`s("hh*8").degradeBy(0.2)`

- struct

`note("c,eb,g")
  .struct("x ~ x ~ ~ x ~ x ~ ~ ~ x ~ x ~ ~")
  .slow(2)`

- mask

`note("c [eb,g] d [eb,g]").mask("<1 [0 1]>")`

- palindrome

`note("c d e g").palindrome()`

## sophisticated rhythms

- linger

`s("lt ht mt cp, [hh oh]*2").linger("<1 .5 .25 .125>")`

- euclid

`note("c3").euclid(3,8)`

### Small assignment for next week! Create a 2 min livecoding set using ONLY ONE SAMPLE. Documentation due as always.

## [Signal Modifiers](https://strudel.cc/learn/signals/)

## ["Random" Modifiers](https://strudel.cc/learn/random-modifiers/)

## [Conditional Modifiers](https://strudel.cc/learn/conditional-modifiers/)

## [Accumulation](https://strudel.cc/learn/accumulation/)

## [Pitch Functions](https://strudel.cc/learn/tonal/)

## ["Experimental Step-wise Patterning"](https://strudel.cc/learn/stepwise/)

## [Yes, you may have your own samples & sampler effects](https://strudel.cc/learn/samples/#loading-custom-samples)



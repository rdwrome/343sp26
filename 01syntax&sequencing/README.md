### Headphones?

### Reading?

## tidal cycles & its flavors
- tidal cycles: MOST POWERFUL but needs a lot to get going (not covered in this class but you can do it!)
- minitidal in estuary: less powerful than strudel but you can play with others
- minitidal in strudel: QUITE powerful but you can't play well with others
- in all three of these environments there is a way to run hydra
- [tidal cycles is pattern-based](https://tidalcycles.org/docs/reference/cycles)
- FYI minitidal in strudel is a js wrapper for tidal cycles; tidal cycles is a haskell wrapper for supercollider (my computer music mother tounge)

## [estuary](https://estuary.mcmaster.ca/)
- What's great
  - so accessible
- What's not so great
  - limited functionality

### starter drum samples

`bd sd hh ho hc lt ht mt cp`

### starter pattern commands and syntax
`s` = sound

`" "` = what to fit inside one cycle

`~` = silence

`!` = repeat

`"[ ] "` = what to fit inside one pulse within one cycle

**starter examples**

`s "bd"`

`s "bd hh"`

`s "bd ~ hh"`

`s "bd ~ hh!2"`

`s "[bd*3] ~ hh!2`

**everybody now in solo mode**

### more advanced commands and syntax

`,` = layer these atop one another within one pulse

`/` = play once per cycle specified as integer in the denominator

`[ | ]` = randomly choose from this array per cycle

`<>` = chose the next one from this list per cycle

`?` = random silence

**more examples**

`s "[bd sd, hh hh]"`

`s "bd sd/2 hh/3"`

`s "[bd | sd | hh]*3"`

`s "<bd sd hh>*3"`

`s "hh!16?"`

**everybody now in solo mode**


### euclidean and polymetric rhythms

`( , )` = spread this many pulses over this many pulses per cycle

`{ , }` = this pattern against this pattern per cycle

**even more examples**

`s "bd(7,12)"`

`s "{bd bd bd bd, cp cp hh}"`

### stacks

`stack [s " ",
s " "]`

**stacks of examples**

`stack [
s "bd(7,12)",
s "{bd bd bd bd, cp cp hh}"
]`

**everybody now in solo mode**

### mix

`-- comment out`

`# silence`

`# pan`

`# gain`

`# resonance`

### periodic oscillators

`sine`

`cosine`

`square`

`tri`

`saw`

`isaw`

**eg**

`# pan sine`

### sound bank indicies
- see all the current samples with:
`!localview audiomap`
- `n` for iNdex (unpitched samples) or Note (samples that are or can be pitched) (more on this later)
- if you give a certain number of events and a different number to use for those events from the index, it will try and even it out.
- n for iNdex goes **after** sound; n for Note goes **before** sounds

**eg**

`s "drum:0 drum:1 drum:2 drum:3"` = play drum sample with first index, then second, then third, etc or

`s "drum*4" # n "0 1 2 3"` = sounds same

`s "drum*4" # n "0 1 2"` = not enough values but evens itself out

### notes & scales as clunky sequencers
`n "0 2 4 5" # s "moog"` = notes with numbers

`n "c e g a" # s "moog"` = notes with names, sounds the same as above

`n (scale "bartok" "0 2 4 5") # s "moog"` = special scale notes

`n (run 7) # s "moog"` = hear a run of the whole collection

`s "moog" # n (irand 7)` = randomness with indicies (doesn't work as notes)

#### all the scales
`minPent majPent ritusen egyptian kumai hirajoshi iwato chinese indian pelog prometheus scriabin gong shang jiao zhi yu whole augmented augmented2 hexMajor7 hexDorian hexPhrygian hexSus hexMajor6 hexAeolian major ionian dorian phrygian lydian mixolydian aeolian minor locrian harmonicMinor harmonicMajor melodicMinor melodicMinorDesc melodicMajor bartok hindu todi purvi marva bhairav ahirbhairav superLocrian romanianMinor hungarianMinor neapolitanMinor enigmatic spanish leadingWhole lydianMinor neapolitanMajor locrianMajor diminished diminished2 chromatic`

### chords

`note (arp "updown" "<a'min7 e'dom7>") # s "moog"`

#### all the chords

`major maj aug plus sharp5 six 6 sixNine six9 sixby9 6by9 major7 maj7 major9 maj9 add9 major11 maj11 add11 major13 maj13 add13 dom7 dom9 dom11 dom13 sevenFlat5 7f5 sevenSharp5 7s5 sevenFlat9 7f9 nine eleven 11 thirteen 13 minor min diminish ed dim minorSharp5 msharp5 mS5 minor6 min6 m6 minorSixNine minor69 min69 minSixNine m69 mSixNine m6by9 minor7flat5 min7 flat5 m7flat5 m7f5 minor7 min7 m7 minor7sharp5 min7sharp5 m7sharp5 m7s5 minor7flat9 min7flat9 m7flat9 m7f9 minor7sharp9 m in7sharp9 m7sharp9 m7s9 diminished7 dim7 minor9 min9 m9 minor11 min11 m11 minor13 min13 m13 one 1 five 5 sus2 sus4 seven Sus2 7sus2 sevenSus4 7sus4 nineSus4 ninesus4 9sus4 sevenFlat10 7f10 nineSharp5 9s5 m9sharp5 m9s5 sevenSharp5flat9 7s5f9 m7sharp5flat9 elevenSharp 11s m11sharp m11s`

#### all the arpeggiators

`up down updown downup converge diverge disconverge pinkyup pinkyupdown thumbup thumbupdown`

### time

`slow 2 $ note "c'maj7 f'maj7" # s "moog"` = halftime

`fast 2 $ note "c'maj7 f'maj7" # s "moog"`= doubletime

`every 3 (fast 2) $ note "c'maj7 f'maj7" # s "moog"` = every third cycle, doubletime

`every 2 (rev) $ s "[bd*3] ~ hh*2"` = every second cycle, reverse the pattern

#### metatime **in terminal!!!**
`!setbpm 90` = change the bpm of bno

## BNO
#### change grid **in terminal!!!** with `!presetview twobyfive` to see everyone

### mini-notation comparison
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

-->



## mini-tidal starter pattern commands and [syntax](https://strudel.cc/learn/code/#functions-arguments-and-chaining)
- functions
- parameters/arguments
- chained functions

`s` = sound

`" "` = what to fit inside one cycle

`~` = silence

`!` = repeat

`\\` = comment

**starter examples**

`s ("bd")`

`s ("bd hh")`

`s ("bd ~ hh")`

`s ("bd ~ hh!2")`

**everybody now!**

## [Strudel Tour](https://strudel.cc/)
- console
- reference
- sounds
- (but we'll use `bd sd hh ho hc lt ht mt cp` for now!)

## more advanced mini-tidal commands and [cycles](https://strudel.cc/understand/cycles/)

`?` = randomly silence

`[]` = nest these within one pulse of the cycle

`[ | ]` = randomly choose sample from this array per cycle

`"< >"` = chose the next one from this list per cycle

`,` = layer these atop one another within one cycle

**more examples**

`s ("hh!16?")`

`s "(bd ~ [hh!2]")`

`s ("[bd | hh | sd]!4")`

`s ("<bd hh sd>!4")`

`s ("bd, ~ hh")`

**everybody now!**

## [Sample Selection with Banks](https://strudel.cc/workshop/first-sounds/)

## [CPM/BPM](https://strudel.cc/workshop/first-sounds/)

### Small assignment for next week! Percussion Patch
- Make a mini-tidal percussion patch (only using `bd sd hh ho hc lt ht mt cp`) you're proud of.
- This week and ALWAYS! Document your work in a .md file as outlined in syllabus (what you did, how you did it, creative process, technical process, etc. Can be stream of consciousness but should more or less be in complete sentences).
- Submit percussion patch and documentation in a single .md file (with the mini-tidal code embedded as below) and hand in via GitHub.com + Canvas as outlined in syllabus.

### Good people, do we remember markdown?
- and how to format embedded code within it? Take a look at *this* .md file

```javascript

/* man in finance @by v10101a 
+ "das ist bass" @by enelg,froos
*/

samples({
  finance:  ['man-in-finance/finance_00.wav', 'man-in-finance/finance_01.wav', 'man-in-finance/finance_02.wav', 'man-in-finance/murrayhill.wav']
}, 'github:sandpills/v10101a-samples/main/');


$: n("<1 0>").s("finance").slow(2).clip(1)
  .mask("<1 1 1 0>/4")
  ._punchcard()

$: n("0").s("finance").slow(2).clip(1.4)
  .struct("1(<3 5>,8)")
  .mask("<0 0 0 1>/4").gain(0.8).room(1.2)
  ._punchcard()

$: note("<a1 c2>/2")
.sound("supersaw")
.euclidLegato(9,16)
.ftype('24db')
.lpf(tri.rangex(2000,400).slow(8))
.lpenv(6)
.dist("2:.4")
.echo(2, 1/16, .7)
.mul(gain("[.5 1!3]*4")) //side chain
.add(note("<[0 5]*4 [5 10]*4>"))
._pianoroll()
// .hush()

$: s("oh*16")
  .bank("RolandTR909")
  .decay(sine.range(.2,.4))
  .dist("1:.3")
  .mul(gain("[<0!3 1> .2 1 <0!3 .2>]*4")) //groove
  .mul(gain("[.2 1!3]*4")) //side chain
  .pan(tri.range(.7,.3))
  .hpf(800)
  .room(.1)
  .mask("<0 1>/8")
 ._punchcard()
  // .hush()

$: s("bd*4").bank('RolandTR909').dist("1:1")
.scope()


//babyshark a la mehetabel


const seed = slider(12,0,12,1)

// samples('github:tidalcycles/dirt-samples');

// $: n(irand(26)).struct("x")
// .s("alphabet")
// .room("[0|.2|.4]")
// .gain("1.2")

$: s ("bd!4").bank('mc303')

_$: s("hh!16?").bank('mc303')

_$: s("cp(3,8)").bank('mc303')

$: n ("33 2 1 3 6 9")
  //.degradeBy(0.3)
  .ribbon(seed,1)
  .s("supersaw")
  .scale("f:major")._pianoroll()

$: n ("25 1 2 3")
  //.degradeBy(0.1)
  .ribbon(seed,1)
  .s("supersaw")
  .scale("c:major")
._pianoroll()
  
$: note ("g3 a3 [c4 c4] [c4 [c4 c4][~ c4]]")
  .sound("gm_electric_bass_finger")
  .shape("[0|.2|.4]")
  .gain("2")
  .mask("<1 0 0 0>")._pianoroll()

$: note ("[c4 ~ [c4 c4] c4]!3")
 .sound("gm_electric_bass_finger")
  .shape("[0|.2|.4]")
  .gain("2")
  .mask("<0 1 1 0>")._pianoroll()

$: note ("c4 c4 b3 ~")
  .sound("gm_electric_bass_finger")
  .shape("[0|.2|.4]")
  .gain("2")
  .mask("<0 0 0 1>")._pianoroll()
	  
```
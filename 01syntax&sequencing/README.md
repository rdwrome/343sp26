### Headphones?

### Reading?

## tidal cycles & its dialects
- [tidal cycles is pattern-based](https://tidalcycles.org/docs/reference/cycles)
- FYI tidal cycles is a haskell wrapper for supercollider (my computer music mother tounge)
- tidal cycles: MOST POWERFUL but needs a lot to get going 
- minitidal in estuary: less powerful than strudel but you can play with others!
- minitidal in strudel: QUITE powerful but you can't play well with others
- with/in all three of these environments there is a way to run hydra

## [estuary](https://estuary.mcmaster.ca/)
- What's great
  - so accessible
- What's not so great
  - limited functionality

### starter drum samples

`bd sd hh lt cp`

### starter pattern commands and syntax

`-- comment`

`s` = sound

`" "` = what to fit inside one cycle

`~` = silence

`!` = repeat

`[]` = what to fit inside one pulse within one cycle

`,` = layer these atop one another within one cycle

'/' = play once per cycle specified as integer in the denominator

`[ | ]` = randomly choose from this array per cycle

`< >` = chose the next one from this list per cycle

`?` = randomly silence

**some examples**

`s "[bd sd, hh hh]"`

`s "bd sd/2 hh/3"`

`s "[bd | sd | hh]!3"`

`s "<bd sd hh>!3"`

`s "hh!16?"`

**everybody now in solo mode**

### stacks

`stack [s " ",
s " "]`

**stacks of examples**

`stack [
s "{bd bd bd bd, cp cp hh}",
s "bd(7,12)"
]`

**everybody now in solo mode**

### mix

`# silence`

`# gain`

`# pan`

`# resonance`

### periodic oscillators

`sine`

`cosine`

`square`

`tri`

`saw`

`isaw`

### sound bank indicies
- see all the current samples with:
`!localview audiomap` HOW DO WE GET OUT???

- `n` for iNdex (unpitched samples) or Note (samples that are or can be pitched) (more on this later)
- if you give a certain number of events and a different number to use for those events from the index, it will try and even it out.
- n for iNdex goes **after** sound; n for Note goes **before** sounds

**eg**

`s "drum:0 drum:1 drum:2 drum:3"` = play drum sample with first index, then second, then third, etc or

`s "drum!4" # n "0 1 2 3"` = sounds same

`s "drum!4" # n "0 1 2"` = not enough values but evens itself out

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

```slow 2 $ note "c'maj7 f'maj7" # s "moog"``` = halftime

`fast 2 $ note "c'maj7 f'maj7" # s "moog"`= doubletime

`every 3 (fast 2) $ note "c'maj7 f'maj7" # s "moog"` = every third cycle, doubletime

#### metatime **in estuary terminal!!!**
`!setbpm 90` = change the bpm 

### Small assignment for next week! Percussion Patch
- Make a minitidal percussion patch (only using `bd sd hh lt cp`) you're proud of.
- This week and ALWAYS! Document your work in a .md file as outlined in syllabus (what you did, how you did it, creative process, technical process, etc. Can be stream of consciousness but should more or less be in complete sentences).
- Submit percussion patch and documentation in a single .md file (with the minitidal code embedded) and hand in via GitHub.com + Canvas as outlined in syllabus.

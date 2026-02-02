
## percussion patches!

## BNO
#### change grid **in terminal!!!** with `!presetview twobyfive` to see everyone

### minitidal comparison
```
// estuary
stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",s
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

// tidal cycles
d1 $ stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  s "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  s "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  s "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] "
]

```

## [Strudel Tour](https://strudel.cc/)
- console
- reference

## minitidal starter pattern commands and [syntax](https://strudel.cc/learn/code/#functions-arguments-and-chaining)
- functions
- parameters/arguments
- chained functions

`\\` = comment

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

**starter examples**

`s ("bd")`

`s ("bd hh")`

`s ("bd ~ hh")`

`s ("bd ~ hh!2")`

**everybody now!**


## [CPM/BPM](https://strudel.cc/workshop/first-sounds/)

## [Sample Selection with Banks](https://strudel.cc/workshop/first-sounds/)

## samples vs synths
- sawtooth square triangle sine

### note vs n
- With Samples: note means 'take this one sample but slow/speed it up to pitch it down and up and play the pitches as notes'
- With Samples: n means iNdex, so it was which sample from the index you wanted to play
- With Synths: note workes best with pitch names
- With Synths: n works best with scales

## [noted](https://strudel.cc/workshop/first-notes/)

- define by pitch name

`note ("c3").sound("sawtooth")`

- sequence away

`note ("c2 d3 e2").sound("sawtooth")`

- sequence over multiple cycles

`note ("[c3 d3 e3]/4").sound("sawtooth")`

- play one in the carrots per cycle in sequence

`note ("c2 <c 3d e2> e3").sound("sawtooth")`

- scale (use `n`)

`n("0 2 4 6 4 2").scale("C:major").sound("sawtooth")`

- elongate

`n("[4@2 3] [5@2 4] [6@2 5]")
.scale("C:ritusen")
.s("sine")`

- scale with rand.range and segment

`n(rand.range(0,12).segment(8))
.scale("C:major")
.s("sine")`

- patterns in parallel with orbit

`$: s("bd sd")
$: note("c eb g")`

## livecoding evaluation!

`
// command-/
//$: s("bd!4").bank('RolandTR909')

_$: n("[0 .. 8]!8/9").scale("C:minor:pentatonic")
` 
## [effects](https://strudel.cc/learn/effects/)

- gain

`s("bd").gain(0.6)`

- pan

`s("bd").pan("<.5 1 .5 0>")`

- crush

`s("<bd sd>,hh*3").fast(2).crush("<16 8 7 6 5 4 3 2>")`

- vowel

`note ("c <c d e> e").sound("sawtooth").lpf("<400 500>").vowel("<a e i o u>")`

- lpf/hpf, room
`
// @title dash on the train @by todepond [mehetabel edit]

$: note("[C G], <D Fb B C A>*[0.5,2]")
  // .rev()
  .sound("sawtooth").cpm(30).gain(.4)
.lpf("<100 200 300 400 500 600 700 800 900 1000 1100 1200 1300 1400 1300 1200 1100 1000 900 800 700 600 500 400 300 200>/4")
  .room(1)
  // .jux(pan)
  .pan("<0 1>/2")  
.delay(1)
.roomsize("10")

__$: note("F")
  .sound("piano").cpm(30)
  .lpf(800)
  
.slow(".1275").gain(.8)`


## [sophisticated pattern transformations](https://strudel.cc/workshop/pattern-effects/)

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

- linger

`s("lt ht mt cp, [hh oh]*2").linger("<1 .5 .25 .125>")`
	
## [visualizers](https://strudel.cc/learn/visual-feedback/)

- piano roll

`note("c2 a2 eb2")
.euclid(5,8)
.s('sawtooth')
.lpenv(4).lpf(300)
.pianoroll()`

	
### Small assignment for next week! Single Sample Song
- Create a 1-2 min livecoding set using ONLY ONE SAMPLE.
- This week and ALWAYS! Document your work in a .md file as outlined in syllabus (what you did, how you did it, creative process, technical process, etc. Can be stream of consciousness but should more or less be in complete sentences).
- Submit minitidal code and documentation in a single .md file (with the minitidal code embedded) and hand in via GitHub.com + Canvas as outlined in syllabus.
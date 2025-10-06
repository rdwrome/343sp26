## percussion patches!

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
_$: n("[0 .. 8]!8/9").scale("C:minor:pentatonic")

// command-/
//$: s("bd!4").bank('RolandTR909')`

**everybody now!**

## share a synth sequence

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


- fast, slow

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
	
### what are euclidean rhythms?
-- poly meter? poly rhythm?...euclidean rhythm?
-- https://www.youtube.com/watch?v=bKazVnHh2w4 (@1:55)

- euclid

`note("c3").euclid(3,8)`

## Research Presentation Due Next Week!
**Research Presentation**
- 7 min. presentation on a SPECIFIC livecoding topic of your choice (with instructor preapproval!!!)
- Be SPECIFIC! one artist's creative practice, development of one coding language/tool, one city's algorave scene, one technique, analysis of one particular work
  - can't be Hydra, SuperCollider, Strudel, TidalCyles, miniTidal (uzu languages)
- Documentation for submission of presentation: .md bibliography using [MLA format](https://owl.purdue.edu/owl/research_and_citation/mla_style/mla_formatting_and_style_guide/mla_general_format.html)
**RIGHT NOW IN CLASS**
- A three or four sentence .md topic proposal about what you want to do, and why you want to do it.
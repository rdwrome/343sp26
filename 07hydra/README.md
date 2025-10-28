### Accessibility
- Don't give someone a seizure
- Let your musicians see the screen

# [video synth basics](https://hydra.ojack.xyz/docs/docs/learning/video-synth-basics/)

# [functions](https://hydra.ojack.xyz/functions)
- chained like minitidal in strudel
- [arrow](https://www.w3schools.com/js/js_arrow_function.asp)

## internal sources & output
- osc: rate per second (60 default)
```javascript
osc().out(o0)
```

- solid: r g b ([alpha](https://en.wikipedia.org/wiki/Alpha_compositing)), all 0-1 float
```javascript
solid(0.5, 0.5, 0.5).out(o0)
```

- shape: sides (3 default), radius, smoothing
```javascript
shape().out(o0)
```

- [noise](https://en.wikipedia.org/wiki/Perlin_noise): scale (10 default), offset
```javascript
noise().out(o0)
```

- [voronoi](https://en.wikipedia.org/wiki/Voronoi_diagram): scale, speed, blending
```javascript
voronoi(5).out(o0)

```

- [gradient](https://en.wikipedia.org/wiki/Gradient)
```javascript
gradient().out(o0)
```

## external sources
- initImage
```javascript
s0.initImage("https://upload.wikimedia.org/wikipedia/commons/2/25/Hydra-Foto.jpg")
src(s0).invert().out(o0)
```

- initVideo
```javascript
s0.initVideo("https://media.giphy.com/media/AS9LIFttYzkc0/giphy.mp4")
src(s0).invert().out(o0)
```

- initScreen 
```javascript
s0.initScreen()
src(s0).invert().out(o0)
```

- initCam
```javascript
s0.initCam()
src(s0).invert().out(o0)
```

## synth settings
- render
```javascript
osc().out(o0)
noise().out(o1)
solid().out(o2)
gradient().out(o3)
render()
```

- hush
```javascript
osc().out(o0)
noise().out(o1)
solid().out(o2)
gradient().out(o3)
render()
hush()
```

# [Examples](https://hydra.ojack.xyz)
- roll through examples
- change parameters
- show and tell
- code reuse!

## geometry
- pixelate
```javasscript 
s0.initImage("https://upload.wikimedia.org/wikipedia/commons/2/25/Hydra-Foto.jpg")
src(s0).pixelate().out(o0)

- kaleid
```javascript
s0.initCam()
src(s0).kaleid(6).out(o0)
```

		
## color
- color
	- r,g,b,a
```javascript
s0.initCam()
src(s0).color(0.5, 0.6, 0.2, 0.5).out(o0)
```

- invert
- saturate
	- how intense color is
```javascript
s0.initCam()
src(s0).saturate().out(o0)
```

- hue
	- base color
- colorama
	- remaps greyscale to colorscale
- [posterize](https://en.wikipedia.org/wiki/Posterization)
- [shift](https://en.wikipedia.org/wiki/Visible_light_communication#Color_Shift_Keying)
- [brightness](https://en.wikipedia.org/wiki/Brightness)
- [luma](https://en.wikipedia.org/wiki/Luma_(video))
	- cuts off pixels with intensity less than the threshold parameter
- thresh
	- luma but 'color of the bright part of the image is preserved'

	
## blend
- add
```javascript
s0.initCam()
src(s0).thresh().add(osc()).out(o0)
```

- mult
- diff
- layer & mask
	- like a stencil
```javascript
osc(10,0,1).hue(0.5).layer(osc(10,0,1).mask(shape(4,0.5,0.001))).out()
```
	
## modulate
	- modulateRepeat
	- modulateRepeatX
	- modulateRepeatY
	- modulateKaleid
	- modulateScrollX
	- modulateScrollY
	- modulateScale
	- modulatePixelate
	- modulateRotate
	- modulateHue

# [minitidal + hydra in strudel](https://strudel.cc/learn/hydra/)

## [so you don't want to show your code...](https://www.youtube.com/watch?v=b9VS7Q86T-Y&list=PL82ekYXUXbcSDipIPs6Df1YpG6s68WJRu&index=13&t=2s)
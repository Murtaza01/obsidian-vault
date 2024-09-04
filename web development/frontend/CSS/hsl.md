there is three properties to `hsl`

# Hue

is the color wheel, it ranges from 0 to 360
0 being red
360 getting back to red
since its a wheel

200 for example is blue

# saturation (التشبع)

is how much of that color (for example red) you want to have

0 being gray (always)
100% being fully red (or the color you pick)

# lightness

lightness is how white or black the color is, its more like opacity 


# having a base color

we can have a base color (that has the most of whatever hue you pick)

```css
.color{
	color: hsl(60,100%,50%)
}
```


# color intensity

when changing the lightness of a color, we often lost the color intensity (how strong the color look), in this case we actually change the Hue not the lightness (we keep it at 50%) because that's where the color is at full of is use (no black or white is added)

![[Pasted image 20240328002115.png]]

"Don’t rotate the hue more than 20-30°
or it will look like a totally different color instead of just lighter or darker."

![[Pasted image 20240328002516.png]]

![[Pasted image 20240328002541.png]]
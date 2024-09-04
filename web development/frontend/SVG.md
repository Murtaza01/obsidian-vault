Scalable Vector Graphics are file format that depends on math to render the image/shape, unlike (PNG/JPEG) which uses pixels and would lose quality when zooming in.

SVG are code, So you can use external File with the name of .svg or use them inline, in your html.

To create an SVG you need to give it a height and a width
<svg height='100' width='100'>
</svg>
there is few things we could give to our property that would define it, for example:

<svg height='250' width='250'>
<circle r='120' cx='125' cy='125' fill='green' stroke='white' stroke-width=5px />
</svg>
r= radios
cx= center on the X axis 
cy= center on the Y axis
fill = the background color (default as black, to set to white you say 'none')
stroke= the border
stroke-width= the border size

you can use things such as:
<circle />
<rect />
<line />

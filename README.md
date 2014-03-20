tangled
=======
trying to mix jade, stylus, iced 
using [tangle](http://github.com/nassimwu/tangle)

```
doctype html5
html
	head
		title tangled
	body
		.clock
			<<clock
				h3= new Date()
					&
						fixed bottom right
						font-size 20px
						color steelblue
						opacity .4

		each item in [1,2,3,4,5]
			p= item
				&
					display inline-block
					margin 1em

		::clock
			$ = require 'jquery'
			setInterval ->
				$('.clock').html templates.clock()
			, 1000

		::
			d3 = require 'd3'
			d3.selectAll('p').data([1..5]).style "font-size", (d)->
				8 * Math.pow(2,d) + "px"

			require 'clock'
```
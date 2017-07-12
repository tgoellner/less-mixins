#LESS MediaQuery mixin
##v1.0
This mixin helps you using CSS MediaQueries in your LESS files. You can chose from a set of predefined breakpoints to change your CSS layout when the browser reaches a minimum width ([Mobile First](https://web3canvas.com/what-is-mobile-first-responsive-design/)).

###Example usage:
	.element {
	    .mq(min-l, {
	        background: #00ff00;
	    }
	}

Results in:

	@media (min-width: 47.5em) {
	    .element {
	        background: #00ff00;
	    }
	}

### Available breakpoints
You can use follwing predefined breakpoints (defined in the <code>@mq_widths</code> variable):

	xs    / mobile           = 360px device width
	s     / smart            = 480px device width
	m     / mobile-landscape = 640px device width
	l     / tablet           = 760px device width
	xl    / tablet-landscape = 960px device width
	xxl   / desktop          = 1180px device width
	xxxl  / desktop-large    = 1600px device width
	xxxxl / hd               = 1900px device width

So <code>.mq(s)</code> will transpile into <code>@media (min-width: 30em) { }</code>

### Using max-width insteadt of min-width
To use it with max-width you can prefix the breakpoint's name with a <code>max-</code>:

<code>.mq(max-s)</code> will transpile into <code>@media (max-width: 29.999em) { }</code>

### Custom breakpoints
You can also use any number as a breakpoint - keep in mind that it will
be converted to EMs:

<code>.mq(600)</code> will transpile into <code>@media (min-width: 37.5em) { }</code>

<code>.mq(max-600)</code> will transpile into <code>@media (min-width: 37.4999em) { }</code>

### Other media queries
To use any other query just provide it instead of a breakpoint:

<code>.mq(~"screen and (orientation: portrait)")</code> will transpile to
<code>@media screen and (orientation: portrait) { }</code>

As LESS combines multiple media queries into one you can nest them too:

	.element {
	    .mq(min-l, {
	        background: #00ff00;
	        .mq(~"screen and (orientation: portrait)", {
	             font-size: 12px;
	        })
	    }
	}

results in:

	@media (min-width: 47.5em) {
	    .element {
	        background: #00ff00;
	    }
	}
	@media (min-width: 47.5em) and screen and (orientation: portrait) {
	    .element {
	        font-size: 12px;
	    }
	}
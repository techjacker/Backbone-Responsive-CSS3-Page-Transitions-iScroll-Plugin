Backbone-Responsive-CSS3-Page-Transitions-iScroll-Plugin
========================================================

iScroll plugin for the [Backbone Responsive CSS3 Page Transitions Plugin](https://github.com/techjacker/Backbone-Responsive-CSS3-Page-Transitions) (v0.3+)


### Demos
[Demos](http://projects.andrewgriffithsonline.com/#backbone-responsive-CSS3-page-transitions) of the CSS frameworks @ [the project homepage](http://projects.andrewgriffithsonline.com/#backbone-responsive-CSS3-page-transitions)

Demo code available from the [github repo](https://github.com/techjacker/Backbone-CSS3-Page-Transitions-CSS-Frameworks-Demos)


## Getting Started
### 1. Loading the JS + CSS
		<link rel="stylesheet" href="scripts/vendor/backbone.responsiveCSS3transitions.min.css"/>
		<!-- place after the main plugin css so the styles cascade -->
		<link rel="stylesheet" href="scripts/vendor/backbone.responsiveCSS3transitions.iscroll.min.css"/>
	</head>

	<body>

		<!-- order is important to satisfy dependencies -->
		<script src="http://code.jquery.com/jquery-1.7.2.min.js"></script>
		<script src="//cdnjs.cloudflare.com/ajax/libs/underscore.js/1.4.2/underscore-min.js"></script>
		<script src="//cdnjs.cloudflare.com/ajax/libs/backbone.js/0.9.2/backbone-min.js"></script>
		<script src="static/js/vendor/iscroll4.js"></script>

		<script src="backbone.responsiveCSS3transitions.min.js"></script>
		<script src="backbone.responsiveCSS3transitions.min.iscroll.js"></script>


### 2. Make your router inherit from backboneResponsiveCSS3Transitions instead of Backbone.Router

	var threeDRouter = backboneResponsiveCSS3Transitions.extend({...});
	new threeDRouter();

	// your view....
	var myBackboneView = Backbone.View.extend({
		className: 'my-container',
		render: function () {
			this.$el.html('the html of the new page to be inserted');
		}
	});


See rest of set up instructions at [main plugin repo](https://github.com/techjacker/Backbone-Responsive-CSS3-Page-Transitions).



## API Reference

You still have all the functionality of the base plugin but now you get the following exta.

### 1. iScroll Plugin Init Options

	var options = {
		// brand new!
		"iScroll": {
			"activeDefault": true,
			"positionScroller": true,
			"scrollerClass": "myScrollbarOutside",
			"options": {
				"bounce" : false
			}
		},
		// old and boring options...
		"fastClick": window.FastClick,
		"wrapElement": ".wrapper"
	};

	var threeDRouter = backboneResponsiveCSS3Transitions.extend({....});
	threeDRouter = new threeDRouter(options);

@param {options.iScroll}
accepts: object

@param {options.iScroll.activeDefault}
accepts: boolean
default: true
description: do you want iscroll to be enabled at application start up?

@param {options.iScroll.positionScroller}
accepts: boolean
default: false
description: do you want the scroller to be positioned at the edge of the screen? Useful if your wrapping div has outside margins.

@param {options.iScroll.scrollerClass}
accepts: string
description: iScroll will add this classname to the scroller so you can style it how you like

@param {options.iScroll.options}
accepts: object
description: the object passed to iScroll constructor when instantiating

	// ...somewhere in the bowels of backbone.responsiveCSS3transitions.iscroll.js
	// forget about the first param - the plugin takes care of that
	new iScroll('iscroll-wrapper', options.iScroll.options);




### 2. enable/disable the iscroll plugin after instantiation

You can enable/disable the iscroll plugin after instantiation in the following ways:

1. calling the toggle toggleiScrollActive method

		var threeDRouter = backboneResponsiveCSS3Transitions.extend({....});
		threeDRouter = new threeDRouter(options);

		// fire!
		threeDRouter.trigger('threeDTransiScroll.toggleiScroll');

2. triggering 'threeDTransiScroll.toggleiScroll' event on the router

		var threeDRouter = backboneResponsiveCSS3Transitions.extend({....});
		threeDRouter = new threeDRouter(options);

		// called method
		threeDRouter.toggleiScrollActive();


3. passing the options.iScrollActive parameter to the triggerTransition method

		var threeDRouter = backboneResponsiveCSS3Transitions.extend({....});
		threeDRouter = new threeDRouter(options);

		// set trigger transition option
		threeDRouter.triggerTransition(ViewClass, {"iScrollActive" : false});
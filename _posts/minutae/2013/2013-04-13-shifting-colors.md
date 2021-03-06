---
title: Shifting colors (Chameleon)
category: minutae
layout: post
---

<div markdown="1" style="width: 100%; height: 30px; background-color: hsl(  10, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl(  30, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 152, 25%, 53% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 210, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 230, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 270, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 290, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 310, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 330, 90%, 60% );"></div>
<div markdown="1" style="width: 100%; height: 30px; background-color: hsl( 350, 90%, 60% );"></div>

### Update:

Just realized this won't make much sense a few years later if I change the theme
& so ... the JS;

```javascript
/* SHIFTING COLORS ~ Chameleon */

// Initialize object
var Chameleon = {};

Chameleon.noOfColors = 10; // should be in CSS, with the transitions
Chameleon.duration = 4; // should match the transition duration in css

Chameleon.init = function() {

  // Check if we support CSS transitions on the browser
  if ( Modernizr.csstransitions ) {

    // Grab the body, we will be using it a lot
    Chameleon.bodyElement = $("body");

    // ~~ faster than Math.floor() -> http://rocha.la/JavaScript-bitwise-operators-in-practice
    Chameleon.colorT = ~~(Math.random()*Chameleon.noOfColors);
    Chameleon.changeColor();
  }
  // Defaults to @orange and @skyblue on hover if we aren't doing this.
}

// Switch colors
Chameleon.changeColor = function() {
  Chameleon.bodyElement.removeClass( 'color' + Chameleon.colorT % Chameleon.noOfColors );
  Chameleon.colorT++;
  Chameleon.bodyElement.addClass( 'color' + Chameleon.colorT % Chameleon.noOfColors );
  setTimeout( Chameleon.changeColor, Chameleon.duration * 1000 );
};

// Get ready, set ... GO!
Chameleon.init();
```

The CSS (necessary bits only);

```css
a {
    -webkit-transition: color 4.0s linear;
    -moz-transition: color 4.0s linear;
    -o-transition: color 4.0s linear;
    transition: color 4.0s linear;
}

.color0 a { color: hsl(  10, 90%, 60% ); } // 1
.color1 a { color: hsl(  30, 90%, 60% ); } // 2
.color2 a { color: hsl( 152, 25%, 53% ); } // 3
.color3 a { color: hsl( 210, 90%, 60% ); } // 4
.color4 a { color: hsl( 230, 90%, 60% ); } // 5
.color5 a { color: hsl( 270, 90%, 60% ); } // 6
.color6 a { color: hsl( 290, 90%, 60% ); } // 7
.color7 a { color: hsl( 310, 90%, 60% ); } // 8
.color8 a { color: hsl( 330, 90%, 60% ); } // 9
.color9 a { color: hsl( 350, 90%, 60% ); } // 10
```

---

1. [Metafizzy: Business end](http://metafizzy.co/) of [David
   Desandro](http://desandro.com/) - he deserves the credit for the idea of
   changing font colors site-wide
2. [Tilde (~~) or the Floor?](http://rocha.la/JavaScript-bitwise-operators-in-
   practice) - hint: tilde is faster
3. [Modernizr: CSS3 feature detection](http://modernizr.com/docs/#features-css)

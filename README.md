Color-commando
==============
This program gives you acces to lowlevel color math in a neat and programmer friendly command line interface.

If you know what you want out of your color math, using a color picker and applying effects one at a time simply takes to long.


Installation
============
```
npm install
```

Yes, node is a prerequisite. If you are a web developer you [installed it already](https://github.com/joyent/node/wiki/Installation), didn't you?

color-commando installs a binary called `color`. If your node binaries are in your `$PATH` you should be all set now.

Usage
=====
Examle:
```
$ color 123456 mix 222 desaturate hex
#202e3c
```

The general usage of `color` follows this pattern:
`color <input> [<modifiers>*] [<outputformat>]`

*Input* is required and can take one of the following forms:
* [Basic](http://www.w3.org/TR/css3-color/#html4) or [Extended](http://www.w3.org/TR/css3-color/#svg-color) color keyword
* `#123456`: Hexadecimal notation. `#` is optional
* `#123`: CSS shorthand for hexadecmal. Translates to `#112233`. `#` is optional
* `rgb(0,0,0)`: CSS RGB notation. No spaces please
* `rgba(0,0,0)`: CSS RGBA notation. No spaces please
* `hsl(0,0,0)`: CSS HSL notation. No spaces please
* `hsla(0,0,0)`: CSS HSLA notation. No spaces please
* `hsv(0,0,0)`: CSS HSV notation. No spaces please
* `hsva(0,0,0)`: CSS HSLV notation. No spaces please

*Modifiers* are optional and can be one of the following:
* Color space channel getter/setter/modifier

  `<channel>` will return the value of the color channel (float [0;1])
  `<channel> <value>` will set the channel to the spceified value (float [0;1])
  `<channel> <value> true` will modify the value of the channel by ±(float [0;1])

  Available channels:
    * `red` or `r`
    * `green` or `g`
    * `blue` or `b`
    * `hue` or `h`
    * `saturation` or `s`
    * `value` or `v`
    * `lightness` or `l`
    * `cyan` or `c`
    * `magenta` or `m`
    * `yellow` or `y`
    * `black` or `k`
    * `alpha` or `a`

* Convenience functions

  For any of these functions taking an `amount` argument, `amount` is optional in the range [0;1] and defaults to 0.1.
    * `lighten [<amount>]`: Makes the color lighter
    * `darken [<amount>]`: Makes the color darker

    * `saturate [<amount>]`: Saturates the color
    * `desaturate [<amount>]`: Desaturates the color

    * `clearer [<amount>]`: Makes the color more transparent
    * `opaquer [<amount>]`: Makes the color less transparent

    * `greyscale`: Converts the color to greyscale
    * `grayscale`: Converts the color to greyscale with english spelling ;)

    * `negate`: Negates the color
    * `mix <othercolor> [<weight>]`: Mixes color and othercolor by the given optional weight. Defaults to 0.5
    * `rotate <degrees>`: Rotates the hue by [0;360] degrees on the hue circle
    * `toalpha <othercolor>`: Converts othercolor to alpha in the original color

*Output format* is optional and can be any of the following
* `hex`: Returns the color value in hexadecimal notation. `#123456`
* `css`: Returns the color value in CSS RGB-notation. `rgb(red, green, blue)`
* `cssa`: Returns the color value in CSS RGBA-notation with alpha channel. `rgba(red, green, blue, alpha)`
* `json`: Returns the color vlaue serialized as a json array with a syntax that [one-color](https://github.com/One-com/one-color) understands. Useful for not losing precision across serialization.
* `equals <othercolor> [<epsilon>]`: Return the string true if color equals othercolor within the optional margin epsilon (defaults to `1e-10`)

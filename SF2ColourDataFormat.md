# Introduction #

Each colour entry in a Street Fighter 2 palette is stored using a 16 bit data structure, also apparently used by NEO-GEO (and possibly other 68k cpu based computers). This document describes the format of said data structure.


# Details #

**Basic format**

As with most palettes used for display on a screen/monitor, the colours in a SF2 palette are stored with separate values for the Red, Green and Blue colour channels.

Four bits are used per colour channel, meaning only 16 values are permissible for each, giving a total of 4096 possible colours representable by the SF2 format.

For non-byteswapped ROMs (some versions of SF2 use this, for example World Warrior), the values are stored as XRGB, giving 16 bits used per colour stored. To the best of my knowledge, SF2 ignores the values in X, and they are always the value 0 in legitimate Capcom ROMs. Some bootlegs store F instead.

For example, a value of 0F00 is entirely red, and 00EC would be a mix of green and blue.

Byteswapped ROMs (SF2T being one) therefore store the data natively as GBXR. 000F is therefore entirely red, and EC00 the same mix of green and blue as in the earlier example.


**Conversion**

Converting from a standard 32bit RGB value is fairly simple, divide each colour channel's value by 16 (rounding down), then convert to a hexadecimal value.

For example, an RGB channel value of 255 or 240 would both divide down to 15, which is represented in hexadecimal as F.


**X**

The 4 bits of X are used in some non-SF2 formats to extend the colour depth of each channel (doubling the number of colours representable to 8192). When converting from an RGB value (dividing each channel's value by 16), the remainder is used to determine the value of X.

If the remainder is > 0.5, add the following value to X:
From red channel: 4
From green channel: 2
From blue channel: 1

So rgb(255, 0, 0) would be represented as 004F in SF2T's byteswapped GBXR format.
rgb(247, 0, 0) would be 000F.
rgb(0, 248, 0) would be F020.
and rgb(255, 255, 0) would be F06F.



The windows tool RGB\_W2N is very useful for converting from RGB to GBXR format, and also allows picking a colour underneath the mouse cursor.
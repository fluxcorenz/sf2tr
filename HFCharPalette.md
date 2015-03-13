# Introduction #

All you need to know about editing Street Fighter 2 Turbo (931202ETC revision) character palettes.


# Details #

## Palette editing notes: ##

16 colours in each character palette.

Each colour in the palette is represented by 2 bytes in the format Green/Blue/unused/Red. So 000F is full red, 0F00 is full blue. This is because the ROM contains byteswapped data - when reordered it is xRGB like you might expect (which is how it looks in the MAME debug memory viewer).

Leave the first colour (2 bytes) in any palette alone, they control transparency and can really make things weird if mucked with.

There are two tools I know of which make editing palettes easy, I recommend trying SF2Pal because, well, I wrote it.

### SF2Pal ###

If your browser supports HTML5 canvas (tested in Safari and Chrome), try http://fluxcore.blogspot.com/p/sf2pal.html for an in-browser palette editor supporting all the characters in SF2T. It also shows the current palette in ROM format, either byteswapped or not, for easy inclusion in a ROM hack. Care should still be taken to not include the first (transparent) colour entry.

### PALMOD: ###

PALMOD allows for easy palette modification for a few Capcom arcade games. Unfortunately it currently does not support SF2T, but can still be useful for editing palettes.

You will need the "sfxe.04a" file from the ssf2t ROM, and the CPS2-enabled PALMOD from http://versuscolors.com/palmod.zip

In PALMOD, File->Load File and select from the filetype dropdown "SSF2T (sfxe.04a)", then locate the file.

Select the desired character from the dropdown box at the lower right.
"Select All" (ctrl-A) to select all the colours in the current palette
Paste a PALMOD string to set the palette.

Edit the various colours by clicking the colour to edit (which becomes surrounded with a red border), then use the "Get Color" button to find a colour. "Set color" sets the colour in the palette and will update the image. The "blink" button is useful for determining which region will be edited.

**NOTE** don't edit the first (0th) colour (top left box), this controls transparency and will cause trouble if changed.

To get usable ROM data values from PALMOD, first clone the Google spreadsheet at https://docs.google.com/spreadsheet/ccc?key=0Ahco9rU9mIPpdGFoMi0zY0swMmxrVENUc0gwVDZXanc - the sheet palmod2rom will convert from PALMOD to ROM data format. Select all in PALMOD then copy, and paste into cell A1 of the palmod2rom spreadsheet. Select cells B3->Q3 and copy.


## Editing the ROM to change palettes: ##

First, back up your ROM in case of problems.
Using your favourite Hex editor (e.g. HxD), open the relevant ROM and select the address range specified below for your character (which should select 32 bytes).
You should deselect the first byte (transparent colour), resulting in 30 bytes selected.
Then paste in the last 30 bytes of data from the palette over the selection.
Save, zip your new ROM into a sf2hf.zip then open in Kawaks or similar. Your character should now be your new colour palette.

## Problems? ##

If you've altered the transparent colour in the ROM, you'll probably experience massive graphical glitches on the character you've edited the palette for. Reset the first byte in the range for your character to whatever is in your backup at that address.

## ROM data locations and values: ##

All the below palettes exist in the sf2\_22.bin rom.

**Ryu Palettes**

Default (HF colours) :
| Address | 2DA9E-2DABD |
|:--------|:------------|
| ROM | 00 00 11 01 EC 0F C9 0E A7 0D 86 0C 64 0A 40 07 AB 0A FF 0D EE 0B CE 09 AD 07 8B 05 68 00 EF 0E |
| Palmod | ($1F000F111FFECFEC9FDA7FC86FA64F740FAABFDFFFBEEF9CEF7ADF58BF068FEEF) |

Alt (WW colours):
| Address | 1E6A6-1E6C5 |
|:--------|:------------|
| ROM | 01 00 11 01 D9 0F B8 0F 97 0E 86 0C 65 09 43 06 00 0B FF 0F EC 0E CA 0D A8 0B 87 0A 65 07 00 0F |
| Palmod | ($1F001F111FFD9FFB8FE97FC86F965F643FB00FFFFFEECFDCAFBA8FA87F765FF00) |

**E.Honda palettes**

Default (HF colours) :
| Address | 2DABE-2DADD |
|:--------|:------------|
| ROM | 00 00 22 02 FE 0F EB 0F C9 0E A7 0C 85 09 64 07 40 05 78 06 FA 0F D4 0F 90 0E 60 0C 00 0A B7 08 |
| Palmod | ($1000002220FFE0FEB0EC90CA709850764054006780FFA0FD40E900C600A0008B7) |

Alt (WW colours) :
| Address | 1E6C8-1E6E7 |
|:--------|:------------|
| ROM |01 00 22 02 EC 0F D9 0F B7 0F 96 0E 64 0B 43 08 31 06 78 06 FF 0D CE 0A AD 08 7C 07 58 06 43 0D |
| Palmod |($1000102220FEC0FD90FB70E960B640843063106780DFF0ACE08AD077C06580D43) |

**Blanka palettes**

Default (HF colours) :
| Address | 2DADE-2DAFD |
|:--------|:------------|
| ROM | 00 00 11 01 FC 0F E0 0F C0 0F 90 0E 60 0C 40 0B 30 05 CE 0A AD 08 7C 07 6B 06 49 05 AC 0A 78 07 |
| Palmod | ($1000001110FFC0FE00FC00E900C600B4005300ACE08AD077C066B05490AAC0778) |

Alt (WW colours):
| Address | 1E6EA-1E709 |
|:--------|:------------|
| ROM | 01 00 11 01 FC 0F E7 0E C4 0D 90 0A 70 08 50 06 30 05 C0 0F 80 0F 60 0D 40 0A 30 08 AC 0A 78 07 |
| Palmod | ($1000101110FFC0EE70DC40A900870065005300FC00F800D600A4008300AAC0778) |

**Guile palettes**

Default (HF colours) :
| Address | 2DAFE-2DB1D |
|:--------|:------------|
| ROM | 00 00 30 06 FD 0F DA 0F B8 0F 86 0D 64 0A CF 07 9F 04 6D 02 39 01 00 0C 7F 04 D0 0F 42 09 26 01 |
| Palmod | ($1000006300FFD0FDA0FB80D860A6407CF049F026D01390C00047F0FD009420126)|

Alt (WW colours) :
| Address | 1E70C-1E72B |
|:--------|:------------|
| ROM | 01 00 40 06 FF 0F D9 0F B8 0F 97 0E 75 0B FA 0D D9 08 97 06 74 04 50 0F 7D 00 E0 0F 64 09 50 00 |
| Palmod | ($1000106400FFF0FD90FB80E970B750DFA08D9069704740F50007D0FE009640050) |

**Ken palettes**

Default (HF colours) :
| Address | 2DB1E-2DB3D |
|:--------|:------------|
| ROM | 00 00 11 01 FB 0F D9 0F A7 0E 86 0D 65 0A 43 06 E6 0F 6F 08 3F 08 1C 07 0B 06 08 05 06 04 C0 0F |
| Palmod | ($1000001110FFB0FD90EA70D860A6506430FE6086F083F071C060B050804060FC0) |

Alt (WW colours):
| Address | 1E72E-1E74D |
|:--------|:------------|
| ROM | 01 00 11 01 FB 0F D9 0F A7 0E 86 0D 65 0A 43 06 E6 0F 60 0F 40 0F 00 0F 00 0C 00 09 00 06 C0 0F |
| Palmod | ($1000101110FFB0FD90EA70D860A6506430FE60F600F400F000C00090006000FC0) |

**Chun Li palettes**

Default (HF colours):
| Address | 2DB3E-2DB5D |
|:--------|:------------|
| ROM | 00 00 00 04 EB 0F D9 0F C8 0F A7 0E 85 0C 64 0A 50 08 30 06 66 06 88 08 AA 0A CC 0C EE 0E FF 0F |
| Palmod | ($1000004000FEB0FD90FC80EA70C850A6408500630066608880AAA0CCC0EEE0FFF) |

Alt (WW colours):
| Address | 1E750-1E76F |
|:--------|:------------|
| ROM | 01 00 00 00 EA 0F C9 0F 97 0E 86 0C 65 0A 50 08 40 07 00 05 09 00 5B 00 8D 05 AE 07 CF 0A FF 0F |
| Palmod | ($1000100000FEA0FC90E970C860A650850074005000009005B058D07AE0ACF0FFF) |

**Zangief palettes**

Default (HF colours):
| Address | 2DB5E-2DB7D |
|:--------|:------------|
| ROM | 00 00 11 01 40 07 65 0B 87 0D BA 0F DD 0F 98 0E 99 04 CC 07 EF 0A 90 0B D7 0F 77 00 54 08 98 0A |
| Palmod | ($10000011107400B650D870FBA0FDD0E98049907CC0AEF0B900FD7007708540A98) |

Alt (WW colours):
| Address | 1E772-1E791 |
|:--------|:------------|
| ROM | 01 00 11 01 40 06 75 0A A7 0D EB 0F FD 0F C9 0E 00 0A 44 0D 66 0F 90 0B D7 0F 00 07 54 08 98 0A |
| Palmod | ($10001011106400A750DA70FEB0FFD0EC90A000D440F660B900FD7070008540A98) |

**Dhalsim palettes**

Default (HF colours):
| Address | 2DB7E-2DB9D |
|:--------|:------------|
| ROM | 00 00 11 01 30 06 50 08 70 0A 90 0C B7 0E EB 0F FF 0F CD 09 34 02 45 03 56 04 78 06 9A 08 CD 0B |
| Palmod | ($100000111063008500A700C900EB70FEB0FFF09CD0234034504560678089A0BCD) |

Alt (WW colours):
| Address | 1E794-1E7B3 |
|:--------|:------------|
| ROM | 01 00 11 01 31 06 53 08 75 0A 97 0C B9 0E DB 0F FF 0F AA 0A 30 0F 30 06 60 09 A0 0C D0 0F F8 0F |
| Palmod | ($100010111063108530A750C970EB90FDB0FFF0AAA0F30063009600CA00FD00FF8) |

**Balrog (boxer) palettes**

Default (HF colours):
| Address | 1E1C2-1EAE1 |
|:--------|:------------|
| ROM | 01 00 55 0D 31 06 53 09 75 0B 96 0C B7 0E EA 0F 66 0E 99 0F 20 0C 50 0E A4 0F C6 0F E8 0F FF 0F |
| Palmod | ($100010D55063109530B750C960EB70FEA0E660F990C200E500FA40FC60FE80FFF) |

Alt (WW colours):
| Address | 1E91A-1E939 |
|:--------|:------------|
| ROM | 01 00 55 0D 31 06 53 09 75 0B 96 0C B7 0E EA 0F 66 0E 99 0F 79 06 9D 06 BE 09 DE 0B EF 0D FF 0F |
| Palmod | ($100010D55063109530B750C960EB70FEA0E660F990679069D09BE0BDE0DEF0FFF) |

**Vega (claw) palettes**

Default (HF colours):
| Address | 1EAE4-1EB03 |
|:--------|:------------|
| ROM | 01 00 22 02 FF 0F EB 0F C9 0E A7 0C 84 0A 60 08 40 06 F6 0F 88 08 66 06 44 04 00 00 E0 00 90 00 |
| Palmod | ($1000102220FFF0FEB0EC90CA70A84086006400FF6088806660444000000E00090) |

Alt (WW colours):
| Address | 1E93C-1E95B |
|:--------|:------------|
| ROM | 01 00 22 02 FE 0F EA 0F B8 0F 96 0E 75 0C 54 09 40 07 F0 0F 9F 0B 7E 09 5B 07 29 04 80 0F 00 0C |
| Palmod | ($1F001F222FFFEFFEAFFB8FE96FC75F954F740FFF0FB9FF97EF75BF429FF80FC00) |

**Sagat palettes**

Default (HF colours, white/red shorts):
| Address | 1EA60-1EA7F |
|:--------|:------------|
| ROM | 03 00 00 0F 00 0A B9 0E 86 0C 62 0A 43 08 30 06 20 03 FF 0F CA 0D A8 0B FE 0F CA 0D A8 0B 76 09 |
| Palmod | ($100030F000A000EB90C860A620843063003200FFF0DCA0BA80FFE0DCA0BA80976) |

Alt (WW colours, purple/red shorts):
| Address | 1E8B8-1E8D7 |
|:--------|:------------|
| ROM | 03 00 00 0F 00 0A C9 0F A8 0D 96 0B 74 09 53 07 30 05 FF 0F BB 0B 77 07 5F 07 3A 05 07 04 05 00 |
| Palmod | ($100030F000A000FC90DA80B960974075305300FFF0BBB0777075F053A04070005) |

**M.Bison (dictator) palettes**

Default (WW colours, red w/grey armour):
| Address | 1E95E-1E97D |
|:--------|:------------|
| ROM | 08 00 34 02 00 06 00 09 32 0C 65 0E 87 0F 56 04 7F 00 EF 0E AD 0A 79 06 D9 0F 96 0E 64 0A 43 06 |
| Palmod | ($100080234060009000C320E650F870456007F0EEF0AAD06790FD90E960A640643) |

Alt (HF colours, grey w/red armour):
| Address | 1E7B6-1E7D5 |
|:--------|:------------|
| ROM | 08 00 00 05 55 05 88 08 BB 0B DD 0D FF 0F 00 07 7F 00 77 0F 44 0C 00 0A ED 0F B9 0D 76 0A 43 06 |
| Palmod | ($100080500055508880BBB0DDD0FFF0700007F0F770C440A000FED0DB90A760643) |


## How I found this: ##

Other versions of the ROMs are likely to have different addresses for this same data, so here's a couple of methods of locating the data in another ROM.

First, if you have another game which contain the same palettes, and know the addresses in that game ROM, you can easily copy the values from that game and find them in your game ROM using a hex editor. You may need to change the order due to byteswapping or similar.

For example, the Street Fighter 2 CE contains the World Warrior colour palettes, which also exist in the SF2T rom as alternate palettes. I knew where those values existed in the CE ROM thanks to Drakon's SF2CE hack project (http://16bitgamer.forumotion.ca/t78-my-custom-street-fighter-2-sheng-long-arcade-hack), so could easily find them in the SF2T rom using the above method.

The HF specific colours are another story - obviously they aren't in CE, so I have to find them without that help.

Using RGB\_W2N (http://www.d1.dion.ne.jp/~kuma_yeb/rgb_w2n.html) to pick colours out of the HF palette manually I was able to recreate parts of each character's palette in PALMOD and then find them in the ROM data using a hex editor.

In this fashion I located the default and alternate palettes of each character.
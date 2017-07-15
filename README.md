# O-knob!

**O-knob! library is a very simple knob/parameter page system and preset manager for Critter & Guitari’s Organelle. Just pick up your value where it was last time, and save it !**

The main.pd is a very simple dual osc / dual lfo synth example with two pages of parameters and one page of preset save and recall for you to experiment with.

Have fun !

**Pros**
* enough for Organelle-only usage
* simple to use (i think)
* light
* can make an awful lot of Organelle patches much better !
* make your mind about which parameters you want to save
* no sudden value jump, no value crossfeed between pages
* scale and offset your values according to use : who needs to display a 10^-6 precision always-changing number ? This is for your synth, not for the user !
* no need to patch your display messages twice as with most other page system attempts!
* once your pot value is overridden by a recall, its LOCKED. It won’t move until you want it to move.

**Cons (by design)**
* won’t work atm if you open two o-knob enabled patches, because you can’t isolate two different o-knob systems, though for recall only it should work well.
* can only save floats (ie no native preset names, though you could easily display one)
* saves pot position [0:1], not your carefully-crafted scaled and offset value.

I’m open to suggestion about modifications, though i really think it’s enough for my use and most Organelle patches.

If you ever need a crazy full-featured state-saving system, i highly recommend kollabs/ds : https://github.com/m—w/kollabs

## CHANGELOG for v2.1
* better thresholding when reaching extreme values
* actually saves presets in the pd file (added [menusave<) :o)

## CHANGELOG for v2
* Added [threshold 0.001] to prevent pot noise
* Changed pick-up method from “we’re close enough” to “we’re past the old value”, fast dialing is now possible
* Removed need for tolerance argument :
* COMPATIBILITY BREAK : **IF YOU REPLACE V1 WITH V2, PLEASE REMOVE ALL TOLERANCE ARGUMENTS (typically 0.02) OTHERWISE IT WON’T WORK**
* Moved existing documentation to example patch

## KNOWN ISSUES
* Due to the [threshold], it’s sometimes (really rarely) hard to pick extreme values as 0.99707 in [0:0.99707]

## TO DO
* save presets outside the patch (txt file-s)
* non-saved parameters should be allowed to jump instead of waiting user to reach stored value
* make it a state machine
* remove all user doc from browsing and presets
* make real help files
* make browsing and presets abstractions instead of subpatches

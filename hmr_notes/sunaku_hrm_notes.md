Taming home row mods with bilateral combinations
Suraj N. Kurapati
16 October 2022
1 January 2024
For the past 2 years, I’ve used home row mods designed by the legendary Miryoku, where the Super, Alt, Control, and Shift modifier keys are embedded in the home row as dual role “mod-tap” keys through my programmable keyboard’s QMK firmware.

Home row and standard modifiers on a typical 60% keyboard.

These keys behave normally when tapped, sending their assigned character (such as the letter “A”) to the computer. But when held, they become modifier keys, sending their assigned modifier (such as Alt or Shift) to the computer instead.

This literally puts all modifier keys at your fingertips, thereby eliminating the need to move your fingers away from the home row to reach them.

Problem
Same-hand chords
Dual-hand chords
Typing streaks
Solution
Patches
Example
rules.mk
config.h
Usage
Allowing same-sided combinations
Allowing crossover combinations
Delaying modifier activation
Suppressing modifiers while typing
Porting to ZMK
Bilateral combinations enforcement
Snippet
Problem
The main issue with home row mods is the unintended activation of modifiers. When typing quickly, I sometimes press keys together like a piano chord instead of tapping and releasing keys individually like distinct notes on a piano scale. This can activate home row mods and trigger unwanted shortcuts on my computer, such as launching an app, closing a window, or sending an unfinished e-mail. 😱

Over time, the negative feedback from these misfires has trained me to type more slowly and thoughtfully, burdening my mind with uncertainty that impedes my natural typing rhythm and unconscious flow of thoughts onto the computer screen.

Same-hand chords
When typing the word “clock” in the Engram layout, I tend to chord “ck” by first holding down “c” with my left pinky finger, tapping “k” with my left index finger, and finally releasing them both simultaneously or in the reverse order.

Same-hand chord "ck" in the word "clock".

Miryoku’s experimental “bilateral combinations” feature attempts to solve this problem by suppressing home row mods for chords that begin and end on the same side of the keyboard. This way, it only affects home row mods for chords that cross over to the other side of the keyboard; so they’re bilateral combinations.

However, it has a longstanding bug called “flashing mods” where the Super key would always be sent to the computer for same-hand chords, even though their home row mods should be suppressed. This makes me accidentally trigger the Start Menu when typing words like “clock” and “sock” due to my “ck” chording tendency.

With sleepless determination, I recently fixed this and contributed a patch.

Dual-hand chords
When typing the word “end” in the Engram layout, I tend to chord the entire word by first holding down “e” with my left middle finger and then holding down “n” with right pinky finger, before finally tapping “d” with my right middle finger. The first two keys essentially form a stable base from which the third can be reached. Similarly, I chord “est” in the same way when typing the word “best”.

Dual-hand chord "en" and same-hand chord "nd" in the word "end".

Thanks to the increased typing speed made possible by my “flashing mods” patch for same-hand chords, I was able to make the above observations which revealed a blind spot in Miryoku’s bilateral combinations concept: it only intercepts same-hand home row mods and completely ignores the dual-handed ones!

This seemed like the key to solving the problem, so I plunged in with more sleepless determination and created a new feature called “crossover” bilateral combinations to intercept fast “rolls” that cross over the left/right boundary.

Typing streaks
When typing the word “stress” in the Engram layout, I tend to chord the end of the word (after typing “str”) by first holding down “e” with my left middle finger and then tapping “s” with right ring finger twice. If done too slowly, this will trigger the “es” bilateral combination (which sends the Ctrl-S shortcut to the computer, in my case) instead of tapping “e” and “s” separately.

Dual-hand chord "es" and key repetition in the word "stress".

There is a brilliant solution to this problem in ZMK’s global-quick-tap feature, which cleverly suppresses modifiers during periods of active typing. For instance, in the example above, I tap “r” immediately before the “es” chord: thus, by measuring the amount of time that has passed between the tap and chord, we can detect whether the chord occurred within a typing streak and suppress it!

Duly inspired, I’ve implemented this idea in QMK via a configurable typing streak timeout setting that automatically suppresses home row mods while typing:

#define BILATERAL_COMBINATIONS_TYPING_STREAK_TIMEOUT 160 /* milliseconds */
However, this tends to obstruct the Shift modifier when typing parentheses or punctuation marks such as ! and ? at the end of a sentence; and it requires a dedicated Shift key as a workaround, per @urob’s “timeless” mods for ZMK. So I went further and exempted Shift modifiers from typing streaks in a bitwise mask:

#define BILATERAL_COMBINATIONS_TYPING_STREAK_MODMASK (~MOD_MASK_SHIFT)
And so, with all this, typing feels natural again! No more unconscious fears about accidentally triggering home row mods. 😌 It’s a complete game changer! 🤩

Solution
Armed with my patches for the aforementioned problems, I have finally tamed home row mods! But how does it even work, you ask? Well, it’s all quite coincidental:

Can’t see SVG image? Try the PNG image, PDF document, or source file.Flowchart: Miryoku's flowchart Combinations for Home Row Mods in QMK

Three main user actions drive the logic: tapping, holding, and releasing keys. Everything happens depending on what keys they hold and how long they hold them.

The green hexagons are external events representing a user’s actions.
The blue ovals are a chord’s main stages of life: begin, extend, end.
The pink folders are #define settings, documented individually below.
The yellow components are QMK functions, which I treat as system calls.
The gray boxes are internal storage mutations that track state changes.
Patches
Apply the following patch or check out a ready-to-use branch or working example.

Patch #56. Endgame: multi-mod crossover chords and typing streaks for:
QMK: Consolidated patch or ready-to-use branch with a working example
Vial: Consolidated patch or ready-to-use branch with a working example
This patch supersedes my previous patches, listed below, by adding support for chord tapping (multiple mod keys) and “eager mods” for mod-click mouse usage.

Obsolete: Patch #54. Crossover combinations for dual-hand chords and rolls
Obsolete: Patch #48. Unilateral mod-tap shouldn’t send GUI to the computer
Example
Below are the relevant parts of my configuration that put everything in action, producing the best typing experience I’ve felt since adopting Miryoku. Enjoy! 😎

rules.mk
DEFERRED_EXEC_ENABLE = yes
config.h
/* QMK */
#define TAPPING_TERM 200
#define IGNORE_MOD_TAP_INTERRUPT /* for rolling on mod-tap keys */

/* Miryoku */
#define BILATERAL_COMBINATIONS
#define BILATERAL_COMBINATIONS_LIMIT_CHORD_TO_N_KEYS 4 /* GUI, Alt, Ctrl, Shift */
#define BILATERAL_COMBINATIONS_DELAY_MODS_THAT_MATCH MOD_MASK_GUI
#define BILATERAL_COMBINATIONS_DELAY_MATCHED_MODS_BY 120  /* ms */
#define BILATERAL_COMBINATIONS_ALLOW_CROSSOVER_AFTER 80   /* ms */
#define BILATERAL_COMBINATIONS_ALLOW_SAMESIDED_AFTER 3000 /* ms */
#define BILATERAL_COMBINATIONS_TYPING_STREAK_TIMEOUT 160  /* ms */
#define BILATERAL_COMBINATIONS_TYPING_STREAK_MODMASK (~MOD_MASK_SHIFT)
Usage
To enable bilateral combinations:

Add the following line to your config.h file:

#define BILATERAL_COMBINATIONS
Add the following line to your rules.mk file to enable QMK’s deferred execution facility.

DEFERRED_EXEC_ENABLE = yes
Allowing same-sided combinations
To enable same-sided combinations (which start on one side of the keyboard and end on the same side, such as RSFT_T(KC_J) and RCTL_T(KC_K) in the abbreviation “jk” which stands for “just kidding”), add the following line to your config.h and define a value: hold times greater than that value will permit same-sided combinations.

For example, if you typed RSFT_T(KC_J) and RCTL_T(KC_K) faster than the defined value, the keys KC_J and KC_K would be sent to the computer. In contrast, if you typed slower than the defined value, the keys RSFT(KC_K) would be sent to the computer.

#define BILATERAL_COMBINATIONS_ALLOW_SAMESIDED_AFTER 500
Allowing crossover combinations
To enable crossover bilateral combinations (which start on one side of the keyboard and cross over to the other side, such as RSFT_T(KC_J) and LGUI_T(KC_A) in the word “jam”), add the following line to your config.h and define a value: hold times greater than that value will permit crossover bilateral combinations.

For example, if you typed RSFT_T(KC_J) and LGUI_T(KC_A) faster than the defined value, the keys KC_J and KC_A would be sent to the computer. In contrast, if you typed slower than the defined value, the keys RSFT(KC_A) would be sent to the computer.

#define BILATERAL_COMBINATIONS_ALLOW_CROSSOVER_AFTER 75
Delaying modifier activation
To delay the registration of certain modifiers (such as KC_LGUI and KC_RGUI, which are considered to be “flashing mods” because they suddenly “flash” or pop up the “Start Menu” in Microsoft Windows) during bilateral combinations, you can define a BILATERAL_COMBINATIONS_DELAY_MODS_THAT_MATCH setting specifying which modifiers should be delayed, and a BILATERAL_COMBINATIONS_DELAY_MATCHED_MODS_BY setting specifying how long that delay (measured in milliseconds) should be.

Add the following line to your config.h and define a bitwise mask that matches the modifiers you want to delay. For example, here we are defining the mask to only match the GUI and ALT modifiers.

#define BILATERAL_COMBINATIONS_DELAY_MODS_THAT_MATCH (MOD_MASK_GUI|MOD_MASK_ALT)
Add the following line to your config.h and define a timeout value (measured in milliseconds) that specifies how long modifiers matched by BILATERAL_COMBINATIONS_DELAY_MODS_THAT_MATCH should be delayed. For example, here we are defining the timeout to be 100 milliseconds long.

#define BILATERAL_COMBINATIONS_DELAY_MATCHED_MODS_BY 100
Suppressing modifiers while typing
To suppress mod-tap holds within a typing streak, add the following line to your config.h and define a timeout value: a typing streak ends when this much time passes after the last key in the streak is tapped. Until such time has passed, mod-tap holds are converted into regular taps. The default value of this definition is 0, which disables this feature entirely. Overall, this feature is similar in spirit to ZMK’s global-quick-tap feature.

#define BILATERAL_COMBINATIONS_TYPING_STREAK_TIMEOUT 175
If you wish to target only certain modifiers (instead of all possible modifiers) for the typing streak timeout setting described above, add the following line to your config.h and define a bit mask: only those modifiers that match this mask will be governed by the typing streak timeout. For example, to exempt Shift modifiers from the typing streak timeout while still targeting all other modifiers, you can specify the following mask.

#define BILATERAL_COMBINATIONS_TYPING_STREAK_MODMASK (~MOD_MASK_SHIFT)
Porting to ZMK
I switched to a new keyboard powered by ZMK firmware recently and I feared it might take another 6 months to rewrite my QMK-based solution described thus far. Fortunately, I was able to port an essential subset of my QMK patches without having to modify ZMK source at all: I didn’t need to write a single line of C++!

By declaratively defining “custom behaviors” in ZMK, I was able to configure home row mods disambiguation using a combination of these behavioral components:

flavor="tap-preferred" for strictly time-based home row mods activation
flavor="balanced" for short-circuiting sequence-based layer activation
hold-trigger for cross-hand home row mods enforcement (positional hold-tap)
tapping-term-ms for home row mods detection, as governed by flavor setting
quick-tap-ms for automatic key repetition via “tap then hold” usage pattern
require-prior-idle-ms timeout for typing streak enforcement
The resulting ZMK configuration is posted here, with documentation in comments. It has separate custom behaviors per hand for crossover bilateral combinations; as well as per thumbs, index fingers, and the rest for differences in dexterity.

compatible = "zmk,behavior-hold-tap";
flavor = HOMEY_HOLDING_TYPE;
hold-trigger-key-positions = <OPPOSITE_HAND_KEYS THUMB_KEYS>;
hold-trigger-on-release; // wait for other home row mods
tapping-term-ms = <HOMEY_HOLDING_TIME>;
quick-tap-ms = <HOMEY_REPEAT_DECAY>;
require-prior-idle-ms = <HOMEY_STREAK_DECAY>;
//
// HOMEY_HOLDING_TYPE defines the flavor of ZMK hold-tap behavior to use
// for the pinky, ring, and middle fingers (which are assigned to Super,
// Alt, and Ctrl respectively in the Miryoku system) on home row keys.
//
#ifndef HOMEY_HOLDING_TYPE
#define HOMEY_HOLDING_TYPE "tap-preferred"
#endif

//
// HOMEY_HOLDING_TIME defines how long you need to hold (milliseconds)
// home row mod keys in order to send their modifiers to the computer
// (i.e. "register" them) for mod-click mouse usage (e.g. Ctrl-Click).
//
#ifndef HOMEY_HOLDING_TIME
#define HOMEY_HOLDING_TIME 270 // TAPPING_TERM + ALLOW_CROSSOVER_AFTER
#endif

//
// HOMEY_STREAK_DECAY defines how long you need to wait (milliseconds)
// after typing before you can use home row mods again.  It prevents
// unintended activation of home row mods when you're actively typing.
//
#ifndef HOMEY_STREAK_DECAY
#define HOMEY_STREAK_DECAY 230
#endif

//
// HOMEY_REPEAT_DECAY defines how much time you have left (milliseconds)
// after tapping a key to hold it again in order to make it auto-repeat.
//
#ifndef HOMEY_REPEAT_DECAY
#define HOMEY_REPEAT_DECAY 300 // "tap then hold" for key auto-repeat
#endif
To illustrate, here is a table of varying behaviors per hand and finger as arranged in Miryoku’s “G-A-C-S” order on the Engram keyboard layout’s home row.

Left Pinky	Left Ring	Left Middle	Left Index	(Finger)	Right Index	Right Middle	Right Ring	Right Pinky
LGUI	LALT	LCTRL	LSHFT	(Hold)	LSHFT	LCTRL	LALT	LGUI
C	I	E	A	(Tap)	H	T	S	N
Specifically, since index fingers are the most dexterous, the normal rules don’t apply to them well. They roll, tap, and hold rapidly and quite differently based on your typing rhythm and use-case. So the “balanced” flavor of hold-tap in ZMK wasn’t the best choice for them as I sometimes roll with my index fingers, which ends up triggering mods when I don’t intend to. Moreover, the “balanced” flavor’s requirement to release the modified (shifted in my case since I use shift on index fingers) key breaks my rhythm and speed when typing CamelCase variable names: I want it to trigger the mod instantly in this case. Instead, the strictly time-based “tap-preferred” flavor seems to better encapsulate their inconsistent complexity (sometimes I want tap, other times I want hold). And that’s essentially what my QMK implementation does, effectively reading my mind.

Bilateral combinations enforcement
💁 Refer to my keymap in the Glove80 Layout Editor for implementation.

The way I’ve implemented bilateral combinations is with 2 levels of hold-taps bridged by a layer transition. The first level starts at the base layer, with the first home row mod that you hold taking you its respective layer on the second level. For example, holding the LeftIndex key takes you to the LeftIndex layer, which masks all same-sided keys with either (1) additional hold-taps for the remaining home row mods or (2) mod-cancelling taps for other remaining keys.

Effectively, this approach constructs a “sandwich” 🥪 of timing thresholds:

You hold the first modifier for at least HOMEY_HOLDING_TIME milliseconds.

The first modifier is now “registered” (sent to the computer).
You are sent to the first modifier’s corresponding layer in the keymap.
You hold the second modifier for at least CHORD_HOLDING_TIME milliseconds.

The second modifier is now “registered” (sent to the computer).
You can repeat step 2 to add even more modifiers to your multi-mod chord.

You tap a key on the opposite hand.

The tap is now “registered” (sent to the computer) and it’s nested under the modifiers you’re already holding (which have also already been “registered”).
NOTE: If you don’t hold the second modifier long enough at step #2, it will look like a same-sided tap, which will then trigger the bilateral combinations logic:

The first modifier will be released.
The first modifier’s normal keycode will be tapped.
The second modifier’s normal keycode will be tapped.
Snippet
See contents of the keymap.dtsi file in my Glove80 keymaps repository on GitHub.

Updates
1 January 2024:
I’ve finally implemented bilateral combinations in ZMK! ❤️‍🔥 It’s still a hair shy 🧐 (lacking multi-key chord unrolling during unilateral cancellation) compared to my QMK endgame patch, but that’s such a theoretical corner case that I don’t think anyone would actually notice in practice. 🙃 Enjoy!

8 November 2023:
In my ZMK port:

Allow the user to override all #defines at the very top of the “Custom Defined Behaviors” ZMK snippet, by guarding each #define with #ifdef.
27 October 2023:
In my ZMK port, I’ve incorporated the new require-prior-idle-ms feature that was recently merged into ZMK to produce the crispest, most responsive typing I’ve ever experienced outside of the typing layer! 🫰🤯✨ ZMK docs say this can eliminate input lag when typing quickly, and they’re right! 💯

Additionally, what this gives us in terms of configuration is the separation of streak vs. repeat decay timers — specifically for homey mods and index finger shifts, but potentially also for thumbs and any other hold-taps imaginable! ️ Thanks to Bryan Forbes for the use-case behind this.

17 October 2023:
I’ve released version 25 of my ZMK snippet with improved spacebar handling.

Thumb keys: disable retro-tap for all thumb keys except spacebar. The backspace thumb key for cursor layer was accidentally navigating the browser back in history for me sometimes.
Thumb keys: increase hold time to 200ms for non-space thumb keys to avoid layer activation where they map you into &none.
Thumb keys: increase repeat decay time to 300ms for non-space thumb keys so it’s easier to hold backspace for repetition.
Rename INDEX_* settings to SHIFT_* because it’s semantically shift: it needs to be fast regardless of the finger it’s on (not just the indexes). Also rename &thumb_space to &space for same reason.
26 September 2023:
I was able to enable typing streaks for index finger shifts while still maintaining fast activation for CamelCase typing. 😤 Next, I separated index fingers’ typing streak from the other home row mods and fine-tuned the timing per my taste: apparently, 70ms is my magic number… 🪄 it just boosted me to my highest raw speed ever (115) measured with home row mods enabled! 🤩 The typefeel is also very crisp 🫰 now, and I must say that I’m quite pleased with this. 👌 See updated ZMK snippet in the Porting to ZMK section.

19 September 2023:
Still not completely satisfied by the robustness of home row mods disambiguation in my ZMK port, I’ve switched back from the “balanced” flavor of hold-tap to the purely time-based “tap-preferred” flavor in order to be more in line with my endgame QMK patch… and oh my, am I impressed! 😍

This change has significantly improved typing responsiveness (less delay from keystroke to letter showing up on the computer screen) and also increased my confidence in the home row mods disambiguation system. 😎👌 I mean, typing is fun now — it’s unexpectedly satisfying to see letters appear instantly on the screen when I press a key. 👏 Hooray for latency! ✨

16 August 2023:
I have added a ZMK port of my QMK patches for home row mods disambiguation.

5 March 2023:
Inspired by ZMK’s global-quick-tap feature, I’ve implemented a typing streak timeout setting that suppresses home row mods while actively typing.

#define BILATERAL_COMBINATIONS_TYPING_STREAK_TIMEOUT 160  /* ms */
However, this obstructs the Shift modifier when typing parentheses or punctuation marks such as ! and ? at the end of a sentence; and it requires a dedicated Shift key as a workaround, per @urob’s “timeless” mods for ZMK. So I went on to exempt Shift modifiers from typing streaks using a bitmask:

#define BILATERAL_COMBINATIONS_TYPING_STREAK_MODMASK (~MOD_MASK_SHIFT)
With all this, typing feels natural again! No more unconscious fears about accidentally triggering home row mods. 😌 It’s a complete game changer! 🤩

29 January 2023:
I have fixed some corner cases, simplified the configuration, improved chording support, and upgraded to QMK 0.19.10. Eager mods are now enabled by default (so that mod-clicks Just Work out of the box) but you can delay them via #define settings.

Removed CHORDSIZE setting since it’s now hard-coded to the maximum allowed value in QMK.
Removed EAGERMODS setting since “eager mods” are now always enabled by default.
Renamed EAGERMASK setting to DELAY_MODS_THAT_MATCH and thereby inverted its meaning (it now specifies modifiers that should be delayed, not made eager).
Renamed DEFERMODS setting to DELAY_MATCHED_MODS_BY.
Renamed CROSSOVER setting to ALLOW_CROSSOVER_AFTER.
Renamed SAMESIDED setting to ALLOW_SAMESIDED_AFTER.
For example, here is a diff showing how my personal configuration has changed since my last update to this article and associated set of patches:

-#define BILATERAL_COMBINATIONS_EAGERMODS 1
-#define BILATERAL_COMBINATIONS_EAGERMASK (~MOD_MASK_GUI)
-#define BILATERAL_COMBINATIONS_DEFERMODS 100
-#define BILATERAL_COMBINATIONS_CROSSOVER 75
-#define BILATERAL_COMBINATIONS_SAMESIDED 3000
-#define BILATERAL_COMBINATIONS_CHORDSIZE 4 // one side GUI, Alt, Shift, Control
+#define BILATERAL_COMBINATIONS_DELAY_MODS_THAT_MATCH MOD_MASK_GUI
+#define BILATERAL_COMBINATIONS_DELAY_MATCHED_MODS_BY 100
+#define BILATERAL_COMBINATIONS_ALLOW_CROSSOVER_AFTER 75
+#define BILATERAL_COMBINATIONS_ALLOW_SAMESIDED_AFTER 3000
19 November 2022:
I have added support for chord tapping (multiple mod keys) and “eager mods” for mod-click mouse usage. The overall logic is illustrated visually as a flowchart and the various #define settings are now documented here as well.

This is, by far, the crispest typing experience I’ve felt in years! :)

27 October 2022:
I have replaced the FLASHMODS mask definition with a new DEFERMODS timeout in order to implement Miryoku’s suggestion of (1) suppressing all modifiers as “flashing mods” and (2) registering them later, after a timeout, for mod-click mouse usage.

-#define BILATERAL_COMBINATIONS_FLASHMODS MOD_MASK_GUI
+#define BILATERAL_COMBINATIONS_DEFERMODS 100

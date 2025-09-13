---
tags:
  - "original"
context:
  - "[[Project Spellblade]]"
---

# Project Spellblade - Mechanics

The fundamental gameplay mechanics.

---

<!-- ## Orb Combinations -->
<!---->
<!-- The game features `3` orbs that can be combined to produce different spells and effects. -->
<!---->
<!-- There can be combinations of `1`, `2`, or `3` orbs. -->
<!---->
<!-- The order of orbs does not matter: `QQW == QWQ == WQQ`. -->
<!---->
<!-- | Count      | Combinations | -->
<!-- | ---------- | ------------ | -->
<!-- | **Single** | `3`          | -->
<!-- | **Double** | `6`          | -->
<!-- | **Triple** | `10`         | -->
<!---->
<!-- Total possible combinations: `19` -->
<!---->
<!-- ``` -->
<!-- [q] [w] [e] -->
<!-- [qq] [ww] [ee] [qw] [we] [eq] -->
<!-- [qwe] [qqq] [www] [eee] [qqw] [qqe] [wwq] [wwe] [eeq] [eew] -->
<!-- ``` -->
<!---->
<!-- ## Orb Behavior -->
<!---->
<!-- **Activation**: The player can activate any of the `3` orbs at any time. -->
<!---->
<!-- **Lifetime (UNDECIDED)**: Once an orb is activated, it stays active for `x` seconds. -->
<!---->
<!-- - The idea is that orb activation should probably be cancellable. -->
<!-- - The player might missclick an orb. If there is no way to cancel said orb, then he would be forced to cast it. -->
<!-- - Having a button just for a cancel seems like clunky design. -->
<!-- - If the idea of lifetime is implemented, the duration should not be long. -->
<!-- - New orbs could be made to reset the lifetime of existing orbs. This prevents misses, but can also be annoying if waiting for lifetime to finish. -->
<!---->
<!-- ## Cast -->
<!---->
<!-- Casts the currently activated orbs. -->
<!---->
<!-- The cast result is a spell, as well as an effect after the spell. -->
<!---->
<!-- **Orb Reset**: The cast must always reset any activated orbs. -->
<!---->
<!-- **Empty Cast (UNDECIDED)**: Figure out what to do when the player attempts to cast with no orbs. Possibilities include: -->
<!---->
<!-- - Do nothing. -->
<!-- - Recast the last spell. -->
<!-- - Use the button for something else. -->

## Attack

Melee range attack.


**Spam**: Repeatable with no cooldown. The attack rate should be relatively fast, ever increasing.

- Being able to hold the button down in addition to spamming it is probably a good idea. Should be toggled from settings.

**Effect**: Attacks interact with the effects of spells.

### Rattle

Passive on-hit ministun mechanic.

Breaks the attack swing of light enemies.

**Design**: Allows the player to melee lighter enemies without getting punished for it.

**Default**: Should be enabled by default, or a very early talent.

### Disrupt

Passive on-hit spellcast rattle.

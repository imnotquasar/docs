# Last stand system

The **Last Stand system** adds a more immersive experience when players are downed. Instead of instantly dying, players enter a **critical state** where they can still move slowly, crawl, and interact with their surroundings until they are either revived by medics or finished off.

This feature creates a realistic survival scenario, giving EMS more time to respond and adding tension to roleplay situations.

{% hint style="warning" %}
The **Last Stand system** can be **disabled** from the configuration if you prefer a simpler death mechanic. To do this, set `Config.LastStand = false` in your config file.
{% endhint %}

***

## How It Works

{% stepper %}
{% step %}
### Entering Last Stand

* When a player’s health reaches zero, they don’t immediately die.
* Instead, they collapse into a **wounded state** with a custom death animation.
{% endstep %}

{% step %}
### Movement While Downed

* Players can crawl across the ground to reach safety or signal for help.
* Movement is heavily restricted and slower than normal walking.
{% endstep %}

{% step %}
### Revival or Execution

* If EMS arrives, they can revive the player using medical tools.
* If enemies attack while down, the player can be finished off permanently.
{% endstep %}
{% endstepper %}

***

## Death Animation

The system includes a **custom death animation**:

* The character **falls to the ground** in a dramatic, realistic motion.
* Once on the floor, they can **drag themselves slowly** using arms and body weight.
* The screen applies a **dark red vignette effect**, creating the feeling of fading out.
* A timer and notification appear on screen, showing how long the player has before respawn or total death.

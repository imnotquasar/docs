# Rent Cycle

The rent cycle system governs how room rentals are managed over time, ensuring a realistic and continuous rental experience for players. It operates independently of player activity and server status, providing a persistent environment for motel management.

***

## How the Rent Cycle Works <a href="#how-the-rent-cycle-works" id="how-the-rent-cycle-works"></a>

{% stepper %}
{% step %}
### **Continuous Operation**

The rent cycle runs continuously, even if the player is not logged into the game or if the server is temporarily offline. This ensures that rental obligations remain consistent and realistic.
{% endstep %}

{% step %}
### **Unique Rent Cycles for Each Playe**

Every player has a personalized rent cycle, allowing for tailored rental durations and payment schedules.
{% endstep %}

{% step %}
### **Room Freezing**

If a player reaches the halfway point of their rent cycle without paying, the room becomes "frozen." While frozen, the room cannot be accessed or used until the rent is paid.
{% endstep %}

{% step %}
### **Unfreezing the Room**

Once the rent is paid, the freeze on the room is lifted, and the player can resume normal access and usage.
{% endstep %}

{% step %}
### **Penalty for Unpaid Rent**

If a player fails to pay the rent entirely, they may be required to pay double the rent as a penalty. This setting is configurable, allowing server administrators to adjust the severity of the penalty based on server rules.
{% endstep %}
{% endstepper %}

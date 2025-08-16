# Change default number

In **config.lua**, you can customize phone numbers using two settings:

{% stepper %}
{% step %}
### Config.Prefix

Specifies the prefix for phone numbers.
{% endstep %}

{% step %}
### **Config.Digits**

Defines the number of digits following the prefix.
{% endstep %}
{% endstepper %}

```lua
Config.NumberPrefix = '553' -- Prefix for the phone number
Config.NumberDigits = 6 -- Number of digits after the prefix
```

Adjust these settings to fit the desired phone number format for your server.

# How to set webhook system

## **Webhook System**

Webhooks are an essential feature for many Quasar Store assets, enabling seamless communication between your server and Discord. They are primarily used to send logs, updates, and other useful information to specific channels in your Discord server.

{% hint style="danger" %}
Please note that if you want to support images and videos, you must use Fivemanage. In case of logs only, you can use Discord. This is due to FiveM API and permissions reasons.
{% endhint %}

***

## **Fivemanage Integration**

Thanks to our collaboration with **fivemanage.com**, you can now upload multimedia content (images, videos, and audio files) securely and efficiently. This system allows for fast uploads and is designed to work seamlessly with Quasar Store assets.

To use fivemanage:

{% stepper %}
{% step %}
### Create your account

Register at [**fivemanage.com**](https://fivemanage.com)**.**
{% endstep %}

{% step %}
### Token Manipulation

Generate a token on the platform.
{% endstep %}

{% step %}
### Add your Token

Add the token to `Config.Webhook` in your asset’s configuration file (e.g., Smartphone or Smartphone PRO).
{% endstep %}
{% endstepper %}

For a detailed tutorial on setting up and using fivemanage, watch this video.

{% embed url="https://www.youtube.com/watch?v=3MMCbAckK1M" %}

***

## **Discord Webhooks**

Discord webhooks are ideal for logging information, such as:

{% stepper %}
{% step %}
### **Server events**

Player joins, bans, purchases, or other server activities.
{% endstep %}

{% step %}
### **System updates**

Notifications related to specific assets.
{% endstep %}
{% endstepper %}

However, due to recent changes in Discord’s terms of service, **webhooks can no longer be used to host images, videos, or audio files** directly. For these capabilities, we recommend using external services like **fivemanage.com**.

For a complete guide on setting up Discord webhooks, watch this video.

{% embed url="https://www.youtube.com/watch?v=fKksxz2Gdnc" %}

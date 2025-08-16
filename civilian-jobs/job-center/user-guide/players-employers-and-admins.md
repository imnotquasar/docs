# Players, Employers & Admins

This section provides a full walkthrough on how different roles interact with **Quasar Job Center** — from players applying for jobs, to bosses managing candidates, to server administrators handling economic integration.

***

## For Players

### **Finding Jobs**

Players can explore job opportunities through the in-game Job Center:

{% stepper %}
{% step %}
**Locate the Job Center blip** on the map (briefcase icon).
{% endstep %}

{% step %}
**Head to the blip location** and find the NPC.
{% endstep %}

{% step %}
**Interact with the NPC** using the targeting system or the default `E` key.
{% endstep %}

{% step %}
**Browse jobs by category** through the intuitive UI.
{% endstep %}

{% step %}
**Click any job card** to see full job details, including salary, description, and requirements.
{% endstep %}
{% endstepper %}

***

### **Applying for Jobs**

Depending on the job’s configuration, players can apply in different ways:

* **Instant Jobs**: Simply click “Apply Now” and you'll be hired immediately — no approval needed.
* **Chat-Based Jobs**: Click the 💬 icon to open a direct conversation with the employer.
* **External Jobs**: The system will redirect the player to an external application, like a Discord server or website.

***

### **Using the Chat System**

For jobs that allow direct communication between players and employers:

{% stepper %}
{% step %}
Click the 💬 icon on the job card.
{% endstep %}

{% step %}
Type your message in the input field.
{% endstep %}

{% step %}
Hit **Enter** or click **Send**.
{% endstep %}

{% step %}
Wait for employer replies — they receive live notifications.
{% endstep %}

{% step %}
Keep an eye out for badge indicators showing unread messages.
{% endstep %}
{% endstepper %}

***

### **Getting Job Locations**

Players can view the physical location of each job role:

* Click the **“Get Location”** button on the job card.
* A **GPS waypoint** will automatically be set on the map.
* Drive or walk to the location to begin your roleplay journey or learn more about the job.

***

## For Employers / Bosses

### **Accessing the Boss Panel**

{% hint style="info" %}
**NOTE:** The player must:

* Be assigned to the job.
* Have the proper grade level defined in the `bossGrades` section of the configuration.
{% endhint %}

Bosses can manage job applications through two methods:

{% stepper %}
{% step %}
### **Via Command:**

```bash
/jobchats
```
{% endstep %}

{% step %}
### **Via Item:**

* Use the `boss_tablet` item from your inventory.
* The item must be present in the inventory to function.
{% endstep %}
{% endstepper %}

***

### **Managing Applications**

Once inside the boss panel:

{% stepper %}
{% step %}
View all jobs you are authorized to manage.
{% endstep %}

{% step %}
See the number of pending applicants and unread messages.
{% endstep %}

{% step %}
Click on each applicant to view the full chat history.
{% endstep %}

{% step %}
Respond to messages in real-time using the built-in chat interface.
{% endstep %}
{% endstepper %}

***

### **Boss Panel Features**

* **Real-time alerts** for new applications.
* **Unread message counters** for each job you manage.
* **Persistent chat history** for ongoing conversation tracking.
* **Multi-job support** – bosses can manage several job roles if permitted.
* **Clean UI navigation** for switching between applicant chats quickly.

***

### For Server Administrators

If you're using an economy or shop system like `qb-shops`, you can make the boss tablet item purchasable:

```lua
-- Example qb-shops configuration
{
    name = 'boss_tablet',
    price = 2500,
    amount = 10,
    info = {},
    type = 'item',
    slot = 20,
}
```

This allows you to monetize or control access to the boss interface through roleplay shops or admin-only vendors.

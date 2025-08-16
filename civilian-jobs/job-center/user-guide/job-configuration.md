# Job Configuration

All job listings in **Quasar Job Center** are fully customizable through `shared/config.lua`. You can organize roles by category, set detailed descriptions, configure salary and requirements, and choose how applications are submitted.

***

## **Job Categories**

Define the categories that jobs will be grouped under in the UI:

```lua
Config.JobCategories = {
    emergency = {
        label = "Emergency Services", -- Display name in UI
        icon = "fas fa-ambulance" -- FontAwesome icon class
    },
    business = {
        label = "Business & Finance", 
        icon = "fas fa-building"
    },
    transport = {
        label = "Transport & Logistics",
        icon = "fas fa-truck"
    },
    -- Add more categories as needed
}
```

These categories help users navigate job listings more easily.

***

## **Job Structure**

Each job must follow a structured format to appear properly in the Job Center:

```lua
Config.Jobs = {
    police = {
        title = "Police Officer", -- Displayed job title
        company = "Los Santos Police Department", -- Organization name
        icon = "fas fa-shield-alt", -- Icon for the job card
        image = "https://images.unsplash.com/photo-1568515387631-8b650bbcdb90?w=600&h=300&fit=crop", -- Optional preview image (600x300 recommended)
        salary = "$4,500 - $6,200", -- Salary text
        status = "High Demand", -- Optional status badge
        category = "emergency", -- Must match a defined category
        description = "Maintain law and order throughout the city. Respond to emergency calls and investigate crimes.", -- Full job description
        requirements = {
            "Clean criminal record", 
            "Valid driver's license", 
            "High school diploma", 
            "Completion of police academy"
        },
        benefits = {
            "Pension plan", 
            "Paid leave", 
            "Health insurance",
            "Equipment provided"
        },
        location = "Mission Row Police Station", -- Location name
        coords = vector3(428.23, -984.28, 30.71), -- Waypoint position
        hasChatbox = true, -- Enable job chat system
        bossGrades = {0, 1, 2}, -- Grades allowed to manage applicants
        applyType = "chatbox" -- Application method
    }
}
```

***

## Application Types

Control how players apply for each job using the `applyType` field:

{% stepper %}
{% step %}
### **Chatbox Applications**

```lua
applyType = "chatbox"
```

* Enables real-time chat between applicants and employers.
* Requires `hasChatbox = true`.
* Only bossGrades defined can reply via the boss panel.
{% endstep %}

{% step %}
### **Instant Applications**

```lua
applyType = "instant"
```

* Automatically hires the player upon application.
* Ideal for entry-level or open-access jobs.
* No interaction or approval required.
{% endstep %}

{% step %}
### **External Link Applications**

```lua
applyType = "link",
applyLink = "https://discord.gg/yourserver"
```

* Redirects the player to a third-party link (e.g., Discord or a web form).
* Useful for jobs with external application requirements or interviews.
{% endstep %}
{% endstepper %}

With these tools, you can build a fully immersive and functional job market tailored to your server’s structure and RP depth.

# Bank Configuration

Quasar Banking allows you to customize physical bank locations, ATMs, and NPC (ped) configurations. This flexibility ensures the system is tailored to your server's layout and gameplay experience. Below is a detailed guide to configuring banks, ATMs, and bank peds.

***

## Configuring Banks and ATMs

### **Bank Locations**

* Add physical bank locations using the `Config.Bank` table.
* Each bank requires:
  * `id`: The bank's identifier, used for blips.
  * `x, y, z`: Coordinates for the bank location.

#### **Example:**

```lua
Config.Bank = { 
    { id = 108, x = 150.266,   y = -1040.203, z = 29.374 },
    { id = 108, x = -1212.980, y = -330.841,  z = 37.787 },
    { id = 108, x = -2962.582, y = 482.627,   z = 15.703 },
    { id = 108, x = -112.202,  y = 6469.295,  z = 31.626 },
    { id = 108, x = 314.187,   y = -278.621,  z = 54.170 }
}
```

### **ATM Models**

* Define ATM models with `Config.ATMModels`.
* Include all prop names for ATMs present in your server.
* If your server uses custom ATM props, simply add their names to the list.

#### **Example:**

```lua
Config.ATMModels = { 
    'prop_atm_01',
    'prop_atm_02',
    'prop_atm_03',
    'prop_fleeca_atm'
}
```

***

## Configuring Peds in Banks

#### **Enable or Disable Peds**

* Use `Config.EnablePeds` to globally enable or disable peds in banks.

#### **Example:**

```lua
Config.EnablePeds = true -- Enable or disable peds at banks
```

#### **Ped Configuration**

* Configure individual peds for each bank.
* Each ped configuration includes:
  * `position`: The ped's location and heading.
  * `model`: The ped model to use.
  * `scenario`: The ped's animation or action (e.g., clipboard).

#### **Example:**

```lua
Config.Peds = {
    {
        position = vector4(149.5513, -1042.1570, 29.3680, 341.6520),
        model = `U_M_M_BankMan`,
        scenario = 'WORLD_HUMAN_CLIPBOARD'
    },
    {
        position = vector4(-1211.8585, -331.9854, 37.7809, 28.5983),
        model = `U_M_M_BankMan`,
        scenario = 'WORLD_HUMAN_CLIPBOARD'
    }
}
```

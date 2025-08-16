# canUsePhone

The **handleClosePhone** event allows you to insert custom logic when the phone is closed. This is useful for triggering specific actions or managing states when the phone is closed.

***

## How to Use

To handle the phone close event, use the following code:

```lua
AddEventHandler('qs-smartphone-pro:handleClosePhone', function(meta)
    -- Add your custom logic here
    print("The phone has been closed.")
end)
```

This event provides flexibility for integrating custom features or behaviors whenever the phone is closed by the player.

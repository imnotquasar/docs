# Telephone booth system

Quasar Smartphone PRO brings a new integrated phone booth system which works through epic cinematics and more dynamically than before.

***

## **Modification of phone booths**

You can manipulate the entire phone booth system by using Config.PhoneBoothBlip for the blips or Config.PhoneBooths for the coordinates of each phone booth. We leave a general configuration here so you can see how the complete system works.

```lua
Config.PhoneBoothBlip = {
    active = true,
    sprite = 459,
    color = 2,
    scale = 0.8,
    name = 'Phone Booth',
}

Config.PhoneBooths = {
    { coords = vec4(128.940659, -2009.749390, 17.013823, 75.118103) },
    { coords = vec4(461.042816, -1852.384643, 26.57, 223.70495605) },
    { coords = vec4(252.936264, -2076.553955, 16.012837, 138.645660) },
    { coords = vec4(378.593414, -2147.301025, 14.601123, 29.094498) },
    { coords = vec4(406.918671, -1613.696655, 27.99307, 141.732285) },
    { coords = vec4(313.621979, -1691.129639, 28.044136, 141.732285) },
    { coords = vec4(38.676926, -1698.527466, 27.999007, 192.755920) },
    { coords = vec4(12.606594, -1532.162598, 27.989907, 48.188972) },
    { coords = vec4(209.723083, -1408.984619, 27.989907, 150.236221) },
    { coords = vec4(48.052750, -1379.274780, 27.979907, 2.834646) },
    { coords = vec4(-342.356049, -1471.872559, 29.465728, 87.874016) },
    { coords = vec4(-37.753845, -1115.314331, 25.132251, 246.614166) },
    { coords = vec4(-227.169220, -943.239563, 27.981307, 68.031494) },
    { coords = vec4(197.261536, -846.659363, 29.513232, 340.157471) },
}
```

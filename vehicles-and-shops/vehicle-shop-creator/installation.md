# Installation

## Script Download

Before starting, you must log in to the CFX portal to download the asset. You will be able to download it as many times as you want on the official CFX page. Just as you download it the first time, you will also download it multiple times in the future to get updates.

{% stepper %}
{% step %}
### Logging in to the CFX Portal

First, log in to the official CFX portal by [clicking here](https://portal.cfx.re/assets/granted-assets).
{% endstep %}

{% step %}
### Finding Your Assets

Once logged in, navigate to the **Granted Assets** section to access your purchased assets. You can download them by clicking the **"Download"** button.
{% endstep %}
{% endstepper %}

Remember, if you encounter any issues or errors when starting the asset, you can check here to see if the problem is related.

{% content-ref url="../../getting-started/what-is-cfx-auth.md" %}
[what-is-cfx-auth.md](../../getting-started/what-is-cfx-auth.md)
{% endcontent-ref %}

<div data-full-width="false"><figure><img src="../../.gitbook/assets/ezgif-5-f03822751d.gif" alt=""><figcaption></figcaption></figure></div>

***

## Downloading Dependencies

The dependencies for this asset are mandatory, so please follow the dependency guide completely and use all required files.

When downloading a dependency, ensure the file is properly unzipped and does not include **"-main"** at the end of its name. If it does, please remove it.

{% stepper %}
{% step %}
### ox\_lib

{% embed url="https://github.com/overextended/ox_lib/releases" %}
{% endstep %}
{% endstepper %}

This script has dependencies depending on its framework, even if it says optional we recommend having them for correct use.

{% stepper %}
{% step %}
## Optional for ESX

{% embed url="https://github.com/esx-framework/esx_addonaccount" %}
{% endstep %}
{% endstepper %}

{% stepper %}
{% step %}
### Optional for QBCore



{% embed url="https://github.com/qbcore-framework/qb-banking" %}

{% embed url="https://github.com/qbcore-framework/qb-management" %}
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/ezgif-5-ee6f842765 (1).gif" alt=""><figcaption></figcaption></figure>

***

## Update artifacts and gamebuild

Updating to the latest **artifacts** and **gamebuild** is essential to avoid common server issues. Here's how to do it properly:

{% stepper %}
{% step %}
### Update Artifacts

> To find the best FiveM artifact, visit [artifacts.jgscripts.com](https://artifacts.jgscripts.com). Thanks to JG Scripts.

Completely replace your current artifacts with the latest version. Download the appropriate artifacts for your operating system from the official links:

* **Windows**: [Windows Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/).
* **Linux**: [Linux Artifacts](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/).
{% endstep %}

{% step %}
### Update Gamebuild

Using gamebuild 3095 is recommended as it is the most stable version, ensuring optimal performance and avoiding compatibility issues.

Edit the `server.cfg` file and add the following line:

```plaintext
sv_enforceGameBuild 3095
```
{% endstep %}
{% endstepper %}

You can see the complete guide to update your server here:

{% content-ref url="../../development-guides/before-you-start/how-to-update-my-server.md" %}
[how-to-update-my-server.md](../../development-guides/before-you-start/how-to-update-my-server.md)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/ezgif-2-2221374386.gif" alt=""><figcaption></figcaption></figure>

***

## Server.cfg Positioning

For best results, place dependencies and \[vehicleshop] in the same folder. If not, ensure dependencies are started before \[vehicleshop] to guarantee proper functionality. This script should always be started under your framework and inventory systems for seamless integration.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

Select the framework you are using and then execute the SQL in your HeidiSQL. If you encounter errors, ensure you are using the most current version of MariaDB. You can refer to our guide above or search online.

<details>

<summary>Database for esx</summary>

```sql
CREATE TABLE IF NOT EXISTS `owned_vehicles` (
    `owner` VARCHAR(64) NOT NULL COLLATE 'utf8mb4_bin',
    `plate` VARCHAR(12) NOT NULL COLLATE 'utf8mb4_bin',
    `vehicle` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb4_bin',
    `impound` INT(1) NOT NULL DEFAULT '0',
    `stored` TINYINT(1) NOT NULL DEFAULT '0',
    `garage_type` VARCHAR(50) NULL DEFAULT 'car' COLLATE 'utf8mb4_bin',
    `garage_id` VARCHAR(50) NULL DEFAULT 'A' COLLATE 'utf8mb4_bin',
    PRIMARY KEY (`plate`) USING BTREE,
    INDEX `vehsowned` (`owner`) USING BTREE
) 
COLLATE='utf8mb4_bin' 
ENGINE=InnoDB;

ALTER TABLE owned_vehicles ADD COLUMN IF NOT EXISTS `garage_id` varchar(32) NOT NULL DEFAULT 'A';
ALTER TABLE owned_vehicles ADD COLUMN IF NOT EXISTS `job` varchar(32) NOT NULL DEFAULT 'civ';
ALTER TABLE owned_vehicles ADD COLUMN IF NOT EXISTS `stored` tinyint(1) NOT NULL DEFAULT 1;
ALTER TABLE owned_vehicles ADD COLUMN IF NOT EXISTS `type` varchar(32) NOT NULL DEFAULT 'car';
```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
CREATE TABLE IF NOT EXISTS `player_vehicles` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `license` varchar(50) DEFAULT NULL,
    `citizenid` varchar(50) DEFAULT NULL,
    `vehicle` varchar(50) DEFAULT NULL,
    `hash` varchar(50) DEFAULT NULL,
    `mods` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL,
    `plate` varchar(15) NOT NULL,
    `fakeplate` varchar(50) DEFAULT NULL,
    `garage` varchar(50) DEFAULT 'pillboxgarage',
    `fuel` int(11) DEFAULT 100,
    `engine` float DEFAULT 1000,
    `body` float DEFAULT 1000,
    `state` int(11) DEFAULT 1,
    `depotprice` int(11) NOT NULL DEFAULT 0,
    `drivingdistance` int(50) DEFAULT NULL,
    `status` text DEFAULT NULL,
    PRIMARY KEY (`id`),
    KEY `plate` (`plate`),
    KEY `citizenid` (`citizenid`),
    KEY `license` (`license`)
) ENGINE=InnoDB AUTO_INCREMENT=1;

ALTER TABLE `player_vehicles`
ADD UNIQUE INDEX UK_playervehicles_plate (plate);

ALTER TABLE `player_vehicles`
ADD CONSTRAINT FK_playervehicles_players FOREIGN KEY (citizenid)
REFERENCES `players` (citizenid) ON DELETE CASCADE ON UPDATE CASCADE;

-- ALTER TABLE `player_vehicles` ADD COLUMN IF NOT EXISTS `balance` int(11) NOT NULL DEFAULT 0;
-- ALTER TABLE `player_vehicles` ADD COLUMN IF NOT EXISTS `paymentamount` int(11) NOT NULL DEFAULT 0;
-- ALTER TABLE `player_vehicles` ADD COLUMN IF NOT EXISTS `paymentsleft` int(11) NOT NULL DEFAULT 0;
-- ALTER TABLE `player_vehicles` ADD COLUMN IF NOT EXISTS `financetime` int(11) NOT NULL DEFAULT 0;
ALTER TABLE player_vehicles ADD COLUMN IF NOT EXISTS `type` varchar(32) NOT NULL DEFAULT 'car';
ALTER TABLE player_vehicles ADD COLUMN IF NOT EXISTS `job` varchar(32) NOT NULL DEFAULT 'civ';

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop
CREATE TABLE IF NOT EXISTS `qs_vehicleshop` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT "Vehicleshop",
  `description` varchar(255) DEFAULT "Description",
  `poly` longtext DEFAULT NULL,
  `height` int(11) DEFAULT 25,
  `spawn_coords` varchar(255) DEFAULT NULL,
  `menu_coords` varchar(255) DEFAULT NULL,
  `show_vehicles` longtext DEFAULT NULL,
  `money` int(255) DEFAULT NULL,
  `shop_job` varchar(50) DEFAULT NULL,
  `boss_id` varchar(50) DEFAULT NULL,
  `up_price_percentage` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `shop_job` (`shop_job`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando datos para la tabla quasar-rolplay.qs_vehicleshop: ~3 rows (aproximadamente)
INSERT INTO `qs_vehicleshop` (`name`, `description`, `poly`, `height`, `spawn_coords`, `menu_coords`, `show_vehicles`, `money`, `shop_job`, `boss_id`, `up_price_percentage`) VALUES
	('Larrys SV Sales', 'Buy your best version!!!', '[{"x":1258.58154296875,"y":2694.584228515625,"z":38.0},{"x":1215.1290283203126,"y":2693.324462890625,"z":38.0},{"x":1216.3221435546876,"y":2741.379638671875,"z":38.0},{"x":1216.5269775390626,"y":2747.39794921875,"z":38.0},{"x":1237.6624755859376,"y":2747.34033203125,"z":38.0},{"x":1237.669189453125,"y":2727.647705078125,"z":38.0},{"x":1240.84619140625,"y":2723.485107421875,"z":38.0},{"x":1244.6849365234376,"y":2722.61328125,"z":38.0},{"x":1251.91357421875,"y":2720.9560546875,"z":38.0},{"x":1253.5516357421876,"y":2716.284912109375,"z":38.0},{"x":1253.6041259765626,"y":2706.133544921875,"z":38.0},{"x":1259.9056396484376,"y":2694.340576171875,"z":38.0}]', 25, '{"x":1250.0343017578126,"y":2713.595947265625,"z":37.00577163696289,"w":13.63076114654541}', '{"x":1224.718505859375,"y":2726.85400390625,"z":38.00426483154297}', NULL, NULL, NULL, NULL, NULL),
	('test', 'test', '[{"x":1104.3135986328126,"y":2680.299560546875,"z":38.0},{"x":1105.906005859375,"y":2692.750732421875,"z":38.0},{"x":1138.6190185546876,"y":2693.23095703125,"z":38.0},{"x":1150.8441162109376,"y":2672.840087890625,"z":38.0}]', 25, '{"w":0.26768192648887,"x":1107.3028564453126,"y":2681.056640625,"z":37.59761047363281}', '{"x":1107.3028564453126,"y":2681.056640625,"z":38.59761047363281}', '[{"model":"zentorno","coords":{"x":1123.2506103515626,"y":2682.09912109375,"z":38.44852828979492},"heading":0.0},{"model":"zentorno","coords":{"x":1119.7691650390626,"y":2682.062744140625,"z":38.48311614990234},"heading":0.0},{"model":"zentorno","coords":{"x":1120.0758056640626,"y":2687.326416015625,"z":38.49858856201172},"heading":0.0},{"model":"zentorno","coords":{"x":1112.5882568359376,"y":2687.7578125,"z":38.57630920410156},"heading":0.0},{"model":"zentorno","coords":{"x":1112.1942138671876,"y":2684.000244140625,"z":38.57381057739258},"heading":0.0},{"model":"zentorno","coords":{"x":1119.7196044921876,"y":2684.889892578125,"z":38.50648498535156},"heading":0.0},{"model":"zentorno","coords":{"x":1123.7181396484376,"y":2684.31689453125,"z":38.46166229248047},"heading":0.0},{"model":"zentorno","coords":{"x":1126.491943359375,"y":2687.63916015625,"z":38.42731475830078},"heading":0.0},{"model":"zentorno","coords":{"x":1130.8160400390626,"y":2687.209228515625,"z":38.37637329101562},"heading":0.0},{"model":"zentorno","coords":{"x":1132.9344482421876,"y":2686.99755859375,"z":38.35694885253906},"heading":0.0},{"model":"zentorno","coords":{"x":1135.2862548828126,"y":2686.7626953125,"z":38.33661651611328},"heading":0.0},{"model":"zentorno","coords":{"x":1126.5184326171876,"y":2687.66943359375,"z":38.42693328857422},"heading":0.0},{"model":"zentorno","coords":{"x":1116.1376953125,"y":2690.74755859375,"z":38.52825927734375},"heading":0.0},{"model":"zentorno","coords":{"x":1109.4056396484376,"y":2690.805908203125,"z":38.60197448730469},"heading":0.0},{"model":"zentorno","coords":{"x":1109.31640625,"y":2685.33251953125,"z":38.61238098144531},"heading":0.0},{"model":"zentorno","coords":{"x":1112.8369140625,"y":2681.555419921875,"z":38.54876708984375},"heading":0.0},{"model":"zentorno","coords":{"x":1118.403076171875,"y":2680.597412109375,"z":38.48503494262695},"heading":0.0},{"model":"zentorno","coords":{"x":1127.5084228515626,"y":2682.2529296875,"z":38.40550231933594},"heading":0.0},{"model":"zentorno","coords":{"x":1130.12060546875,"y":2682.227783203125,"z":38.3813591003418},"heading":0.0},{"model":"zentorno","coords":{"x":1132.8427734375,"y":2682.199951171875,"z":38.3562126159668},"heading":0.0},{"model":"zentorno","coords":{"x":1135.5797119140626,"y":2682.168212890625,"z":38.33733749389648},"heading":0.0},{"model":"zentorno","coords":{"x":1140.916015625,"y":2682.1142578125,"z":38.29116058349609},"heading":0.0},{"model":"zentorno","coords":{"x":1140.9854736328126,"y":2682.11376953125,"z":38.29050064086914},"heading":0.0},{"model":"zentorno","coords":{"x":1138.6182861328126,"y":2682.137939453125,"z":38.31212615966797},"heading":0.0},{"model":"zentorno","coords":{"x":1136.74267578125,"y":2689.388671875,"z":38.30215072631836},"heading":0.0},{"model":"zentorno","coords":{"x":1132.411376953125,"y":2691.17041015625,"z":38.28276443481445},"heading":0.0},{"model":"zentorno","coords":{"x":1129.7984619140626,"y":2691.191162109375,"z":38.31390380859375},"heading":0.0},{"model":"zentorno","coords":{"x":1129.630615234375,"y":2692.0185546875,"z":38.26024627685547},"heading":0.0},{"model":"zentorno","coords":{"x":1124.5574951171876,"y":2692.612548828125,"z":38.31159973144531},"heading":0.0},{"model":"zentorno","coords":{"x":1122.0238037109376,"y":2692.634765625,"z":38.33879852294922},"heading":0.0},{"model":"zentorno","coords":{"x":1119.2923583984376,"y":2692.6611328125,"z":38.36598205566406},"heading":0.0},{"model":"zentorno","coords":{"x":1111.9569091796876,"y":2692.720947265625,"z":38.45314788818359},"heading":0.0},{"model":"zentorno","coords":{"x":1115.610107421875,"y":2680.077880859375,"z":38.51060485839844},"heading":0.0}]', NULL, NULL, NULL, NULL);

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop_mission_data
CREATE TABLE IF NOT EXISTS `qs_vehicleshop_mission_data` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `vehicle_model` varchar(255) DEFAULT NULL,
  `vehicle_coords` varchar(255) NOT NULL,
  `vehicle_health` int(11) NOT NULL,
  `fuel_level` float NOT NULL,
  `delivery_coords` varchar(255) NOT NULL,
  `is_active` tinyint(1) DEFAULT 1,
  `assigned_job` varchar(50) NOT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop_showcase
CREATE TABLE IF NOT EXISTS `qs_vehicleshop_showcase` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `vehicle_id` int(11) NOT NULL DEFAULT 0,
  `x` int(50) DEFAULT NULL,
  `y` int(50) DEFAULT NULL,
  `z` int(50) DEFAULT NULL,
  `h` int(50) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `vehicle_id` (`vehicle_id`),
  CONSTRAINT `FK_qs_vehicleshop_showcase_qs_vehicleshop_stock` FOREIGN KEY (`vehicle_id`) REFERENCES `qs_vehicleshop_stock` (`id`) ON DELETE CASCADE ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop_stock
CREATE TABLE IF NOT EXISTS `qs_vehicleshop_stock` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `vehicleshop_id` int(11) NOT NULL,
  `vehicle_model` varchar(255) DEFAULT NULL,
  `price` bigint(20) DEFAULT NULL,
  `stock` int(11) unsigned zerofill DEFAULT 00000000000,
  `unlimited_stock` int(11) DEFAULT 0,
  `discount` int(11) DEFAULT 0,
  `hidden` int(11) DEFAULT 0,
  PRIMARY KEY (`id`),
  KEY `FK_qs_vehicleshop_vehicles_qs_vehicleshop` (`vehicleshop_id`),
  CONSTRAINT `FK_qs_vehicleshop_vehicles_qs_vehicleshop` FOREIGN KEY (`vehicleshop_id`) REFERENCES `qs_vehicleshop` (`id`) ON DELETE CASCADE ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando datos para la tabla quasar-rolplay.qs_vehicleshop_stock: ~9 rows (aproximadamente)
INSERT INTO `qs_vehicleshop_stock` (`vehicleshop_id`, `vehicle_model`, `price`, `stock`, `unlimited_stock`, `discount`, `hidden`) VALUES
	(1, 'zentorno', 10000, 00000000009, 0, 0, 0),
	(1, 'krieger', 1000000, 00000000009, 0, 0, 0),
	(2, 'zentorno', 10000, 00000000000, 0, 0, 0),
	(2, 'krieger', 10000, 00000000000, 0, 0, 0),
	(2, 'police4', 10000, 00000000000, 0, 0, 0),
	(1, 't20', 232, 00000000018, 0, 10, 0),
	(1, 'futo', 22112123123123, 00000000001, 0, 0, 0),
	(1, 'faggio', 20000, 00000000001, 0, 0, 0),
	(1, 'pigalle', 150000, 00000000001, 0, 0, 0);

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop_transactions
CREATE TABLE IF NOT EXISTS `qs_vehicleshop_transactions` (
  `transaction_id` int(11) NOT NULL AUTO_INCREMENT,
  `shop_id` int(11) DEFAULT NULL,
  `vehicle_model` varchar(100) DEFAULT NULL,
  `buyer_id` varchar(255) DEFAULT NULL,
  `purchase_price` decimal(10,2) DEFAULT NULL,
  `purchase_date` datetime DEFAULT current_timestamp(),
  `payment_method` varchar(50) DEFAULT NULL,
  `vehicle_props` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL CHECK (json_valid(`vehicle_props`)),
  `plate` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`transaction_id`),
  KEY `shop_id` (`shop_id`),
  CONSTRAINT `qs_vehicleshop_transactions_ibfk_1` FOREIGN KEY (`shop_id`) REFERENCES `qs_vehicleshop` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando estructura para tabla quasar-rolplay.qs_vehicleshop_vehicles
CREATE TABLE IF NOT EXISTS `qs_vehicleshop_vehicles` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `vehicle_model` varchar(255) DEFAULT 'zentorno',
  `default_description` text DEFAULT 'This vehicle combines modern design with exceptional performance. With an efficient engine and smooth transmission, it offers a pleasant and agile driving experience. Its interior is spacious and comfortable, ideal for long trips or daily commutes. Equipped with advanced technology and safety features, it guarantees peace of mind on every journey. Perfect for those looking for versatility and style in one package.',
  `min_price` int(255) DEFAULT 1000000,
  `max_price` int(255) DEFAULT 3000000,
  `buy_price` int(255) DEFAULT 1000000,
  `hidden` int(11) DEFAULT 0,
  PRIMARY KEY (`id`),
  UNIQUE KEY `vehicle_model` (`vehicle_model`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- Volcando datos para la tabla quasar-rolplay.qs_vehicleshop_vehicles: ~69 rows (aproximadamente)
INSERT INTO `qs_vehicleshop_vehicles` (`vehicle_model`, `default_description`, `min_price`, `max_price`, `buy_price`, `hidden`) VALUES
	('adder', 'A high-performance supercar with remarkable speed and design. Perfect for thrill-seekers who want both luxury and power.', 1500000, 2500000, 2000000, 0),
	('buffalo', 'A muscle car with a modern twist, combining speed and style. Suitable for city drives or high-speed pursuits.', 300000, 500000, 400000, 0),
	('dominator', 'This classic American muscle car is built for power and performance. It\'s a solid choice for car enthusiasts.', 400000, 700000, 500000, 0),
	('banshee', 'With a sleek design and powerful engine, this sports car is all about speed and handling.', 500000, 900000, 700000, 0),
	('zentorno', 'This vehicle combines modern design with exceptional performance. With an efficient engine and smooth transmission, it offers a pleasant and agile driving experience. Its interior is spacious and comfortable, ideal for long trips or daily commutes. Equipped with advanced technology and safety features, it guarantees peace of mind on every journey. Perfect for those looking for versatility and style in one package.', 1000000, 3000000, 1000000, 0),
	('faggio', 'A small, lightweight scooter that\'s perfect for quick, urban travel. It may not be fast, but it\'s reliable.', 10000, 20000, 15000, 0),
	('kuruma', 'A compact and durable sedan with bulletproof protection. Ideal for heists or evading the cops.', 500000, 800000, 600000, 0),
	('insurgent', 'An armored, off-road beast that can withstand a beating. Perfect for those who want safety and power.', 1200000, 1800000, 1500000, 0),
	('bati801', 'One of the fastest motorcycles on the market, known for its agility and handling.', 100000, 200000, 150000, 0),
	('akuma', 'A nimble and quick bike, great for navigating through the city streets at top speed.', 80000, 150000, 100000, 0),
	('cheetah', 'A luxury sports car that offers both speed and sophistication. Ideal for those who want to make an impression.', 1300000, 2100000, 1700000, 0),
	('vigilante', 'An iconic, weaponized vehicle for those who want to make a statement and pack a punch.', 2500000, 3500000, 3000000, 0),
	('schafter2', 'A luxury sedan with a sporty feel. Great for executives who value both comfort and style.', 600000, 900000, 750000, 0),
	('carbonizzare', 'An elegant sports car with a smooth, powerful ride. Perfect for making a stylish entrance.', 700000, 1000000, 850000, 0),
	('entityxf', 'A high-end hypercar that combines sleek design with extreme speed. Not for the faint of heart.', 1500000, 2500000, 2000000, 0),
	('t20', 'One of the fastest and most expensive supercars in GTA V. Ideal for those with deep pockets and a need for speed.', 2000000, 2800000, 2400000, 0),
	('blista', 'A compact and affordable car, perfect for new drivers or budget-conscious players.', 15000, 30000, 20000, 0),
	('oracle', 'A mid-range luxury sedan that combines comfort and performance, ideal for everyday driving.', 80000, 120000, 100000, 0),
	('dubsta6x6', 'A powerful 6x6 off-road vehicle that can handle any terrain with ease.', 500000, 800000, 650000, 0),
	('rebel', 'An affordable off-road truck, ideal for rugged terrains and tough conditions.', 20000, 50000, 35000, 0),
	('comet', 'A classic sports car with great handling and acceleration. Known for its reliability and sleek design.', 300000, 500000, 400000, 0),
	('f620', 'A luxury coupe that combines power with elegance. Ideal for drivers who value both performance and class.', 400000, 600000, 500000, 0),
	('felon', 'A stylish convertible perfect for cruising through the city. It\'s both luxurious and affordable.', 100000, 200000, 150000, 0),
	('sultan', 'A versatile vehicle that performs well on the streets and off-road. Popular among car enthusiasts.', 200000, 400000, 300000, 0),
	('turismor', 'A high-performance supercar with a lightweight frame and aerodynamic design.', 1500000, 2300000, 1800000, 0),
	('voltic', 'An electric sports car with rapid acceleration and a unique design. Perfect for eco-conscious racers.', 600000, 900000, 750000, 0),
	('brawler', 'An off-road beast that can handle rough terrains with ease. Great for desert or mountain trails.', 400000, 700000, 550000, 0),
	('gauntlet', 'A classic American muscle car with a powerful engine and aggressive design. Ideal for car collectors.', 300000, 500000, 400000, 0),
	('ruiner', 'A retro-inspired sports car with a unique look and solid performance. Great for fans of classic cars.', 250000, 400000, 300000, 0),
	('benson', 'A heavy-duty truck used for transporting goods. Rugged and reliable for any cargo job.', 50000, 100000, 75000, 0),
	('guardian', 'A massive off-road truck that can conquer any terrain. Ideal for those who want power and durability.', 350000, 600000, 450000, 0),
	('moonbeam', 'A classic van with a retro style. Perfect for those who prefer a more vintage look.', 40000, 80000, 60000, 0),
	('sentinel', 'A sleek, mid-range luxury sedan. Known for its comfort and handling on city streets.', 90000, 140000, 120000, 0),
	('massacro', 'A high-end sports car with excellent speed and handling. Great for racing enthusiasts.', 800000, 1200000, 1000000, 0),
	('osiris', 'An elite supercar that combines speed, handling, and unique design. Perfect for luxury car collectors.', 1700000, 2500000, 2000000, 0),
	('xls', 'A luxury SUV that offers both comfort and performance. Ideal for family trips or off-road adventures.', 600000, 900000, 750000, 0),
	('serrano', 'A compact luxury SUV with a sporty look. It\'s both practical and stylish.', 200000, 300000, 250000, 0),
	('patriot', 'A rugged SUV designed for off-road and tough conditions. Known for its durability and power.', 400000, 600000, 500000, 0),
	('cognoscenti', 'An executive sedan that offers both luxury and performance. Perfect for high-profile drivers.', 900000, 1300000, 1100000, 0),
	('baller', 'A mid-range luxury SUV that combines style and performance, perfect for city driving.', 80000, 120000, 100000, 0),
	('manana', 'A classic, vintage car with a unique design. Ideal for those who appreciate retro vehicles.', 30000, 60000, 45000, 0),
	('asea', 'A simple and affordable sedan, ideal for getting from point A to point B without breaking the bank.', 10000, 20000, 15000, 0),
	('pigalle', 'A unique classic sports car with a vintage design. Perfect for those who love classic style.', 70000, 150000, 110000, 0),
	('sabregt', 'A retro muscle car with a powerful engine and stylish look. Great for fans of classic American cars.', 250000, 400000, 300000, 0),
	('nightshade', 'A powerful muscle car with an aggressive design, perfect for those who love speed and style.', 500000, 800000, 650000, 0),
	('windsor', 'A luxury convertible known for its elegance and performance. Ideal for a scenic drive.', 700000, 1000000, 850000, 0),
	('jester', 'A high-end sports car that combines speed with modern design. Great for racers.', 900000, 1300000, 1100000, 0),
	('prototipo', 'Un coche de carreras futurista que ofrece un rendimiento excepcional en pistas. Perfecto para competiciones.', 2000000, 3000000, 2500000, 0),
	('tampa', 'Un muscle car clásico que combina estilo y potencia. Ideal para quienes buscan velocidad y diseño vintage.', 350000, 600000, 450000, 0),
	('vacca', 'Un superdeportivo que destaca por su diseño aerodinámico y su potente motor. Ideal para quienes aman la velocidad.', 1200000, 2000000, 1600000, 0),
	('dilettante', 'Un coche pequeño y económico, perfecto para moverse por la ciudad sin gastar mucho.', 15000, 30000, 20000, 0),
	('tornado', 'Un coche clásico que ofrece un viaje suave y un estilo vintage. Ideal para los amantes de los coches retro.', 30000, 70000, 50000, 0),
	('vamos', 'Una furgoneta robusta y espaciosa, ideal para transporte y trabajos de carga.', 30000, 60000, 45000, 0),
	('jb700', 'Un coche clásico con un diseño elegante y características únicas. Perfecto para quienes aman lo retro.', 500000, 800000, 600000, 0),
	('bifta', 'Un vehículo todoterreno ideal para explorar terrenos difíciles. Perfecto para aventuras al aire libre.', 50000, 90000, 70000, 0),
	('sanchez', 'Una moto todoterreno que ofrece velocidad y maniobrabilidad. Ideal para terrenos irregulares.', 50000, 100000, 70000, 0),
	('hauler', 'Un camión de carga robusto y fiable, perfecto para transportar mercancías pesadas.', 70000, 150000, 100000, 0),
	('granger', 'Una SUV duradera y espaciosa, ideal para la familia y aventuras off-road.', 300000, 500000, 400000, 0),
	('furoregal', 'Un elegante coche deportivo que combina estilo y rendimiento. Perfecto para los amantes de la velocidad.', 600000, 900000, 750000, 0),
	('jesterclassic', 'Un coche deportivo clásico que ofrece un rendimiento excepcional y un estilo atemporal.', 700000, 1000000, 850000, 0),
	('ztype', 'Un coche de lujo con un diseño impresionante y un rendimiento sobresaliente. Ideal para coleccionistas.', 2000000, 3000000, 2500000, 0),
	('michelli', 'Un sedán de lujo con características avanzadas, ideal para viajes de larga distancia.', 800000, 1200000, 1000000, 0),
	('patriotmil', 'Una versión militar de la SUV Patriot, equipada para condiciones extremas.', 600000, 900000, 750000, 0),
	('trophytruck', 'Un vehículo de carreras off-road diseñado para conquistar cualquier terreno.', 900000, 1300000, 1100000, 0),
	('vortex', 'Una motocicleta deportiva que ofrece velocidad y un diseño aerodinámico.', 60000, 120000, 90000, 0),
	('zorrusso', 'Un coche deportivo de lujo que combina estilo y rendimiento. Perfecto para las calles de Los Santos.', 800000, 1200000, 1000000, 0),
	('sultanrs', 'Una versión mejorada del Sultan, con un rendimiento aún más impresionante.', 600000, 900000, 750000, 0),
	('zebra', 'Un vehículo pequeño y ágil, perfecto para moverse rápidamente por la ciudad.', 15000, 30000, 20000, 0),
	('pariah', 'Un coche de superdeportivo conocido por su velocidad y atractivo diseño. Ideal para las carreras.', 1200000, 2000000, 1700000, 0);
```

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>

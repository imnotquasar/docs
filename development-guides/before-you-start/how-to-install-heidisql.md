# How to install HeidiSQL

Here’s a step-by-step guide to downloading and installing MariaDB and HeidiSQL.

***

## Download and Install MariaDB

{% stepper %}
{% step %}
### **Download MariaDB**

* Visit the official [MariaDB website](https://mariadb.org/download/).
* Select your operating system (Windows, Linux, macOS).
* Download the recommended stable version.
{% endstep %}

{% step %}
### **Run the Installer**

* Open the downloaded file and start the installation process.
* Accept the terms and conditions.
{% endstep %}

{% step %}
### **Configuration During Installation**

* Select Components: Ensure "MariaDB Server" and "Command Line Tools" are selected for installation.
* User Setup: Set a password for the `root` user (administrator). Save this password securely.
* Connection Port: The default port for MariaDB is `3306`. Keep this default unless another service is using the same port.
{% endstep %}

{% step %}
### **Complete the Installation**

* Follow the installer’s instructions to finish the setup.
* MariaDB will be installed as a service and will start automatically.
{% endstep %}
{% endstepper %}

***

## Download and Install HeidiSQL

{% stepper %}
{% step %}
### **Download HeidiSQL**

* Visit the official [HeidiSQL website](https://www.heidisql.com/download.php).
* Download the latest version for Windows.
{% endstep %}

{% step %}
### **Run the Installer**

* Open the downloaded file and start the installation process.
* Follow the standard steps (accept terms, choose folder, etc.).
{% endstep %}

{% step %}
### **Set Up a Connection in HeidiSQL**

* Open HeidiSQL after installation.
* Click **"New"** to create a new connection.
* Fill in the fields as follows:
  * **Network Type:** MySQL (TCP/IP).
  * **Hostname/IP:** `localhost` (or your server's IP).
  * **User:** `root`.
  * **Password:** Use the password you set during the MariaDB installation.
  * **Port:** `3306` (or the port you configured for MariaDB).
* Click **"Save"** and then **"Open"** to connect.
{% endstep %}
{% endstepper %}

***

## Visual guide with video

If you haven't done it yet, here is a short installation guide for MariaDB and HeidiSQL.

{% embed url="https://www.youtube.com/watch?v=6QCx0ayBLUQ" %}

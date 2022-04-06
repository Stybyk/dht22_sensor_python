# dht22_sensor_python
DHT22 python sensor + influxdd
SENSOR LIBRARY
https://thepihut.com/blogs/raspberry-pi-tutorials/am2302-temp-humidity-sensor

sudo apt-get update
sudo apt-get install python3-pip
sudo python3 -m pip install --upgrade pip setuptools wheel

sudo pip3 install Adafruit_Python_DHT
pip3 install influxdb




DATABASE CREATION

INFLUX 

CREATE USER admin WITH PASSWORD 'influxadmin' WITH ALL PRIVILEGES

CREATE USER rpi WITH PASSWORD 'rpi'
CREATE DATABASE sensor_data

GRANT ALL ON "sensor_data" TO "rpi"
CREATE USER grafana WITH PASSWORD 'grafana'
GRANT READ ON "sensor_data" TO "grafana"

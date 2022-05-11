# dht22_sensor_python
DHT22 python sensor + influxdd
SENSOR LIBRARY
https://thepihut.com/blogs/raspberry-pi-tutorials/am2302-temp-humidity-sensor

sudo apt-get update
sudo apt-get install python3-pip
sudo python3 -m pip install --upgrade pip setuptools wheel

sudo pip3 install Adafruit_Python_DHT
sudo pip3 install influxdb




DATABASE CREATION

INFLUX 

CREATE USER admin WITH PASSWORD 'influxadmin' WITH ALL PRIVILEGES

CREATE USER rpi WITH PASSWORD 'rpi'
CREATE DATABASE sensor_data

GRANT ALL ON "sensor_data" TO "rpi"
CREATE USER grafana WITH PASSWORD 'grafana'
GRANT READ ON "sensor_data" TO "grafana"



**RASPBERRY PI ZERO ISSUE INFLUXDB API NOT AVAILIBLE EROR - HAPPEN IF RASPBERRY PI START WITHOUT INTERNET AND RANDOM TIME SELECTION CORRUPT DATABASE** 

1)
systemctl stop influxdb

2) Remove all TSI index files
rm -r /var/lib/influxdb/data

3) Rebuild TSI index files
su --command "influx_inspect buildtsi -datadir /var/lib/influxdb/data -waldir /var/lib/influxdb/wal" influxdb

4) Start InfluxDB again
systemctl start influxdb

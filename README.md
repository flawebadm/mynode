# mynode notes by flavio flajs, 06.01.2019
node-red intallatio

- git clone https://github.com/flawebadm/mynode.git

```bash
# after installation of termux and termux api
# run the commands in 
```

```bash
sh -x ./toexecute1.txt
# modify os.cpus()
sh -x ./toexecute2.txt
# modify os.cpus()
```
```bash
pkg install mosquitto
pkg install nodejs
grep -lr "cpus()" /data/data/com.termux/files/usr/lib/node_modules
```

```bash
npm i -g --unsafe-perm node-red
grep -lr "cpus()" /data/data/com.termux/files/usr/lib/node_modules
```

```bash
/* contribute package */
node-red-contrib-termux-api
node-red-contrib-mqtt-broker
node-red-contrib-mqtt-dashboard
```

```bash
/* not required
npm i -g --unsafe-perm pm2
grep -lr "cpus()" /data/data/com.termux/files/usr/lib/node_modules
pip install homeassistant
grep -lr "cpus()" /data/data/com.termux/files/usr/lib/node_modules
*/
```

```bash
# start mosquitto
mosquitto
# address http://ipaddress:1883
#
# start node-red
node-red
# address http://ipaddress:1880
#


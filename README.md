# mynode notes by flavio flajs, 06.01.2019
(nodejs, mosquitto) node-red intallation on termux

- git clone https://github.com/flawebadm/mynode.git

```bash
## google android play store install:
## termux
## termux api
## after installation of termux and termux api
## settings -> app & notifications -> termux
## permissions 
## storage switch to on
## start termux -> upper left corner swipe down termux icon and press "acquire wakelock"
## run the commands in a-first.script.txt
## connect from putty or other ssh client and continue with installation
```

```bash
# some packages installed as described in a-first.script.txt
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

```bash
/* termux-api contribution error
Command: termux-camera-photo [ '-c', '1', '/data/data/com.termux/files/home/tmp_photo.jpg' ]
7 Jan 09:31:40 - [red] Uncaught Exception:
7 Jan 09:31:40 - TypeError [ERR_INVALID_CALLBACK]: Callback must be a function
    at makeCallback (fs.js:143:11)
    at Object.unlink (fs.js:961:14)
    at fs.readFile (/data/data/com.termux/files/home/.node-red/node_modules/node-red-contrib-termux-api/index.js:150:18)
    at FSReqCallback.readFileAfterClose [as oncomplete] (internal/fs/read_file_context.js:53:3)
*/
/* (stop mode-red if not crashed) modify file  /data/data/com.termux/files/home/.node-red/node_modules/node-red-contrib-termux-api/index.js
comment out line 150: /* changed by ff: fs.unlink(photoFile); */
start node-red
*/
```
*/

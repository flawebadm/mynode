# mynode notes by flavio flajs, 06.01.2019
(nodejs, mosquitto) node-red intallation on termux

- git clone https://github.com/flawebadm/mynode.git

```bash
# Google Play Store
# Install Termux https://play.google.com/store/apps/details?id=com.termux&hl=en
# Install Termux:API https://play.google.com/store/apps/details?id=com.termux.api
# Add Privileges:
# 1. Termux
# Settings->Apps & notification->Termux->Permissions:
# Storage 
# 2. Termux:API
# Settings->Apps & notification->Termux:API->Permissions:
# Camera, Contacts, Location, Microphone, SMS, Telephone
# Start Termux
# Swipe down Termux icon on left upper corner and touch "ACQUIRE WAKELOCK"
```

```bash
# Termux terminal window
pkg update
pkg upgrade
pkg install openssh
# start ssh daemon
sshd
# get user info
id
# change password
passwd
# get your ip address
ifconfig
# continue with Termux terminal or connect to Termux session with putty or other ssh client.
```


```bash
## google android play store install:
## termux
## termux api
## after installation of termux and termux api
## settings -> app & notifications -> termux
## permissions 
## storage switch to on
## settings -> app & notification -> termux API
## grant all
## start termux -> upper left corner swipe down termux icon and press "acquire wakelock"
## run the commands in a-first.script.txt
## connect from putty or other ssh client and continue with installation
```

```bash
# some packages installed as described in a-first.script.txt
sh -x ./toexecute1.txt
# modify os.cpus()
/* change all occurences of "os.cpus()" to 1 
   =========================================
/data/data/com.termux/files/usr/lib/node_modules/npm/node_modules/node-gyp/lib/build.js
/data/data/com.termux/files/usr/lib/node_modules/npm/node_modules/worker-farm/README.md
/data/data/com.termux/files/usr/lib/node_modules/npm/node_modules/worker-farm/examples/pi/index.js
/data/data/com.termux/files/usr/lib/node_modules/npm/node_modules/worker-farm/lib/farm.js
*/
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
# mosquitto password
# cd /data/data/com.termux/files/usr/etc/mosquitto
# create txt file (name.txt):
name:password
[name1.password1
...]
# encrypt
mosquitto_passwd -U name.txt
# modify /data/data/com.termux/files/usr/etc/mosquitto/mosquitto.conf
allow_anonymous false
password_file /data/data/com.termux/files/usr/etc/mosquitto/name.txt
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

modify "cpus" errors for pm2:
/data/data/com.termux/files/usr/lib/node_modules/pm2/lib/API/Extra.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/lib/God.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/lib/God/ActionMethods.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/lib/HttpInterface.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/node_modules/@pm2/agent-node/src/utils/meta.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/node_modules/@pm2/agent/src/InteractorDaemon.js
/data/data/com.termux/files/usr/lib/node_modules/pm2/node_modules/@pm2/agent/src/push/DataRetriever.js

pip install homeassistant
grep -lr "cpus()" /data/data/com.termux/files/usr/lib/node_modules
*/
Start at login
pm2 start mosquitto -- -v -c /data/data/com.termux/files/usr/etc/mosquitto/mosquitto.conf
pm2 start node-red --node-args="--max-old-space-size=128" -- -v
pm2 start hass --interpreter=python -- --config /data/data/com.termux/files/home/.homeassistant
pm2 save

pm2 show hass
pm2 logs hass

If you make mistake in pm2 configuration…
pm2 stop {hass or node-red...}
pm2 delete {hass or node-red...}

nano ~/.bashrc
pm2 resurrect
```

```bash
# # # # # # #
# secure with user/passwd mosquitto & node-red
# # # # # # # 
# start mosquitto
mosquitto
# address http://ipaddress:1883
#
# start node-red
node-red
# address http://ipaddress:1880
#
```

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

```bash
# install
npm install -g node-red-admin
# generate hassh passwd
node-red-admin hash-pw
# edit settings.js
vi $HOME/.node-red/settings.js (ca line 130)
    // Securing Node-RED
    // -----------------
    // To password protect the Node-RED editor and admin API, the following
    // property can be used. See http://nodered.org/docs/security.html for details.
    //adminAuth: {
    //    type: "credentials",
    //    users: [{
    //        username: "admin",
    //        password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.",
    //        permissions: "*"
    //    }]
    //},
```
```bash
$ cat start.sh
# ff, 2019-01-08
#
# sshd
#
CNT=$(ps -ef | grep  ' sshd$' | wc -l)
if [ $CNT -gt 0 ]
then
        echo "sshd is running."
else
        echo "sshd is not running, starting ..."
        cd $HOME/start/sshd
        sshd &
        echo "sshd started."
fi
#
# mosquitto
#
CNT=$(ps -ef | grep  ' mosquitto$' | wc -l)
if [ $CNT -gt 0 ]
then
        echo "mosquitto is running."
else
        echo "mosquitto is not running, starting ..."
        cd $HOME/start/mosquitto
        nohup mosquitto &
        echo "mosquitto started."
fi
#
# node-red
#
CNT=$(ps -ef | grep  ' node-red$' | wc -l)
if [ $CNT -gt 0 ]
then
        echo "node-red is running."
else
        echo "node-red is not running, starting ..."
        cd $HOME/start/node-red
        nohup node-red &
        echo "node-red started."
fi
#
cd $HOME
```

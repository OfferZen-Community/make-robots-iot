## Below are some tips and instructions that might help on Make Day :)

### Finding your way around

Inside the `iot_robots` folder you'll find the following:

* An `/activities` folder. If you want to do individual activities then start out here. Some of them have starter code in and some not.

* The `/projects` folder is where you'll do more interesting things like combine different activities or try out one your ideas. There are example projects there and some other ideas you might want to try out. All of this is described in the `README`.

* We've created a Sphero-CLI tool to get you started super quick. Have a look inside `/resources` to find it. The repo is here:
https://github.com/OfferZen-Make/sphero-cli

#### Controlling Sphero

* Our documentation of Sphero's commands is in the readme of the [Sphero-CLI tool](https://github.com/OfferZen-Make/sphero-cli).

* The official SDK has a number of examples that show off what Sphero can do. [Check them out here](https://github.com/orbotix/sphero.js/tree/master/examples)

* The official SDK has a [Javascript API section on their website](https://sdk.sphero.com/community-apis/javascript-sdk/). Makers haven't found this super useful, so try the above two first!

#### List of our Sphero IDs

To connect to your Sphero, you need to tell your Pi which Sphero is yours. On Linux (which is running on the Pi) the argument is the device's MAC address and on macOS it is the Device ID. If your Sphero's Device ID is not in the table below then ask us to help you find it :)


| Sphero Label | Device name	  | MAC address       | Device ID                        |
| -------------| -------------- | ----------------- | -------------------------------- |
| A            | SK-5186        | F8:CC:A1:A7:51:86	| |
| B            | SK-7D19        | FF:AF:08:F6:7D:19	| 3e35859590014eaea8ed68eb3d5874f2 |
| C            | SK-BEAD        | EB:76:90:85:BE:AD	| 38a2cd60b8f14032896de2c9739d5ffe |
| D            | SK-40A2        | F5:77:55:BE:40:A2	| |
| E            | SK-C345        | E0:01:D9:64:C3:45	| |
| F            | SK-D4A7        | FA:34:A8:E7:D4:A7	| 47936f015f7148ae9ed81ef2a08f91b4 |
| G            | SK-0EC0        | FD:94:C6:CA:0E:C0	| |
| H            | SK-70C4        | E8:CC:F3:D0:70:C4	| 6542b255dc1741089e5fa58752f67fea |
| I            | SK-EC32        | C7:8A:28:6D:EC:32	| |
| J            | SK-76D8        | CB:68:ED:5F:76:D8	| |
| K            | SK-2368        | E6:EA:05:40:23:68	| |
| L            | SK-E1F8        | C2:92:5C:11:E1:F8	| |
| O            | SK-5FCA        | F4:C3:EB:77:5F:CA	| |
| P            | SK-E8F5        | C1:EA:BB:43:E8:F5 | |

<!-- | M            | SK-E1F8        | C2:92:5C:11:E1:F8	| 5cb4cdd41c1b4b0b8b5b0c185458b31b | -->

### Version Control and Github

Sharing is good, so contribute to the community by pushing your code to Github! Also, you probably want to have the code on your own Github profile. The `readme` in the `/projects` folder describes how you'll go about doing that.

NOTE: If you have any comments/suggestions about the process above then please send a message to @dan and/or @nuclearnic on Slack :)

### Working on the Pi

* A very lightweight editor you can use is called Geany.

* If you want to install a different editor or extra extensions then go ahead! Remember that not everything you're used to has an ARM-compatible version.

* If your Pi gets a bit slow then try closing some browser windows. If that fails then do a restart!


### Control the Pi with VNC

You might want to code on your own machine and not on the Pi itself. In that case, you can control the Pi from your own machine with VNC. Here's how to do it:

* Click on the VNC icon on the top-right of the control panel

* Note the IP address of your Pi

* Use VNC-Viewer on your own device and connect to the IP Address of your Pi

* You will be asked for a username and password: Enter "pi" and "raspberry" for these

* That´s it!

If you want to `ssh` then that's cool too B-)


### Javascript Snippets that might help

* Chaining mulitple Sphero commands with <i>async/await</i> and delays:

```javascript
async function instructions() {
  orb.color("green")
  await orb.roll(50,180).delay(3000)
  await orb.roll(100,0).delay(3000)
  await orb.roll(200,180)
}
orb.connect(instructions)
```

* Using <i>async/await</i> and delay to calibrate Sphero:

```javascript
async function instructions() {
  // post-calibration instructions
}
async function calibrate() {
  orb.startCalibration();
  await orb.color("red").delay(3000)
  orb.finishCalibration()
  instructions()
}
orb.connect(calibrate)
```

* Using `setInterval` to flash green and red forever:

```javascript
async function flashForever() {
  setInterval(async () => {
    await orb.color("green").delay(1000)
    await orb.color("red")
  }, 2000);
}
orb.connect(flashForever)
```

* When using `setInterval`, you can `clearInterval` to exit the delayed loop. The code below will change Sphero's colour 10 times then exit:

```javascript
async function flashForTenSeconds() {
  let i = 0

  let interval = setInterval(async () => {
    await orb.color("green").delay(1000)
    await orb.color("red")
    console.log(i)
    if(i == 4){
      console.log('how')
      clearInterval(interval)
    }
    i += 1
  }, 2000);
}
orb.connect(flashForTenSeconds)
```

### Additional Info and Resources

* If you want to play around with Gobot, it is already installed. Check out `/home/pi/go/src/gobot.io/x/gobot` and ask the Make Masters for help. Golang is tricky if you haven´t used it before! ;)


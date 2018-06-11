## Below are some tips and instructions that might help on Make Day :)

### Finding your way around

Inside this folder you'll find the following:

* An `/activities` folder. If you want to do individual activities then start out here. Some of them have starter code in and some not.

* The `/projects` folder is where you'll do more interesting things like combine different activities or try out one your ideas. There are example projects there and some other ideas you might want to try out. All of this is described in the `README`.

* We've created a Sphero-CLI tool to get you started super quick. Have a look inside `/resources` to find it. The repo is here:
https://github.com/OfferZen-Make/sphero-cl


### Version Control and Github

Sharing is good, so contribute to the community by pushing your code to Github! Also, you probably want to have the code on your own Github profile. The `readme` in the `/projects` folder describes how you'll go about doing that.

NOTE: If you have any comments/suggestions about the process above then please send a message to @dan and/or @nuclearnic on Slack :)

### Working on the Pi


* We've installed the Pi-compatible version of VS-Code. <b>Note</b> that some Makers have found this a bit slow! You can open it from the Programming section on the Taskbar, or you can open the directory you're in from the command line with the following command:
`$ code-oss .`

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

* Chaining mulitple Sphero commands with <b>promises</b> and delays
```javascript
orb.color("green").roll(50,180).delay(1000).then(() => {
  return orb.color("red").roll(50,270).delay(2000)
}).then(() => {
  return orb.roll(100, 0)
})
```

* Using `setTimeout` to calibrate Sphero
```javascript
orb.startCalibration();
setTimeout(() => {
  orb.finishCalibration();
  // rest of code goes here
}, 3000)
// not here
```

* Using `setInterval` to flash green and red forever.
```javascript
setInterval(() => {
  orb.color("red").delay(500).then(() => {
    return orb.color("green");
  })
}, 1000);
```

* When using `setInterval`, you can `clearInterval` to exit the delayed loop. The code below will change Sphero's colour 10 times then exit.
```javascript
let i = 0

let interval = setInterval(() => {
  orb.color("red").delay(500).then(() => {
    return orb.color("green");
  })

  if (i == 9) {
    clearInterval(interval)
  }

  i += 1
}, 1000);
```

### Additional Info and Resources

* If you want to play around with Gobot, it is already installed. Check out `/home/pi/go/src/gobot.io/x/gobot` and ask the Make Masters for help. Golang is tricky if you haven´t used it before! ;)


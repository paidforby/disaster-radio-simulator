
A javascript network simulator for the [disaster.radio](https://disaster.radio) routing protocol.

![](screenshot.png?raw=true)

This simulator comes in two parts; a locally-run "firmware simulator" that provides console debugging output and a browser-based "visual simulator" that provides a visual representation of the firmware simulation output.

# Firmware simulator
First install dependencies for compiling the C process that is used by the simulator,

```
sudo apt update
sudo apt install libssl-dev # this is the only one i needed
```

Next, compile the firmware,

```
cd routers
make firmware
```

Finally, run the simulator,

```
cd ..
npm install
./simulator.js
```

You can now play around with the network's configuration by modifying the options in `simulator.js`.   

The router firmware can be modified through the `routers/firmware.c` file, you'll need recompile it before re-running the simulator.

The default behavior is for the nodes to learn about their neighbors and for ~100s and then one node, chosen at random, may begin routing packets to other nodes.

If you'd like to know more about the default protocol being used by disaster.radio nodes, read [our wiki](https://github.com/sudomesh/disaster-radio/wiki/Protocol).

# Visual simulator
First install javascript dependencies, if you have not already,
```
npm install
```
Then, build the script,
```
npm run build
```

And, finally, start the server,
```
npm start
```
Be sure to also start `simulator.js` if you haven't already (see above), and open a browser to http://localhost:8000.

You can develop the server using,
```
npm run watch
```
# ToDo
* expand visual interface (e.g. choose which nodes send/receive packets, inspect metrics and routing tables)
* fix various bugs, https://github.com/sudomesh/disaster-radio-simulator/issues

# License and copyright
* Copyright 2018 Sudo Mesh 
* javascript simulator is licensed AGPLv3
* `routers/firmware.c` is dual-licensed under both GPLv3 and AGPLv3

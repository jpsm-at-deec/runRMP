# runRMP

## something on the system:

### uname -r

5.15.0-92-generic

### rosversion -d

noetic

## about the sources:

[segway_rmp](https://github.com/segwayrmp/segway_rmp.git)

[serial](https://github.com/wjwwood/serial.git)

[libsegwayrmp](https://github.com/segwayrmp/libsegwayrmp.git)

## dependencies for gui:

libsdl1.2-dev

qt5-default

## provisional instructions:

git clone

cd 

catkin_make_isolated

source ./install_isolated/setup.bash

./install_isolated/bin/segwayrmp_gui

![segwayRMP DEMO](https://github.com/jpsm-at-deec/runRMP/blob/main/imgs/demo.png?raw=true)

## snippets from a segwayrmp example

...

    #include "segwayrmp/segwayrmp.h"

...

    segwayrmp::SegwayRMP rmp(interface_type);
    
...


    rmp.connect();

    rmp.setOperationalMode(segwayrmp::balanced);
    
    while(true) {
    
      rmp.move(0.1, 0);
      
      usleep(100000);
      
    }
...

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

./src/libsegwayrmp/bin/segwayrmp_interactive_example serial /dev/ttyUSB0

./src/libsegwayrmp/bin/segwayrmp_interactive_example usb index 0

./src/libsegwayrmp/bin/segwayrmp_interactive_example usb serial_number "00000056"

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

--------------------------------------------------------------------------------

        SegwayRMP()
        SegwayRMP::SegwayRMP 	( 	InterfaceType  	interface_type = serial,
        		SegwayRMPType  	segway_rmp_type = rmp200 
        	) 		
        
        Constructs the SegwayRMP object given the interface type.
        
        Parameters
            interface_type	This must be can, usb, or serial. Default is usb.
            segway_rmp_type	This can be rmp50, rmp100, rmp200, or rmp400. Default is rmp200. 

...

        move()
        void SegwayRMP::move 	( 	float  	linear_velocity,
        		float  	angular_velocity 
        	) 		
        
        This command moves the base at a given linear and angular velocity. This assumes the max velocity scalar is set to 1.0.
        
        Parameters
            linear_velocity	Forward/Reverse desired velocity of the vehicle in m/s.
            angular_velocity	Desired angular velocity of the vehicle in degrees/s, positive to is left. 

...

        setOperationalMode()
        void SegwayRMP::setOperationalMode 	( 	OperationalMode  	operational_mode	) 	
        
        Sets the operational mode.
        
        Parameters
            operational_mode	This must be disabled, tractor, or balanced. 

## side note

[Institut de Robòtica i Informàtica Industrial](https://gitlab.iri.upc.edu/labrobotica/drivers/segway_rmp_200/)

    ->right_wheel_velocity
    ->left_wheel_velocity
    ->pitch_angle
    ->pitch_rate
    ->roll_angle
    ->roll_rate
    ->yaw_rate
    ->left_wheel_displ
    ->right_wheel_displ
    ->forward_displ
    ->yaw_displ
    ->uptime
    ->left_torque
    ->right_torque
    ->ui_battery
    ->powerbase_battery

...

    void CSegwayRMP200::init_threads(void)
    {
        this->thread_server = CThreadServer::instance();

        this->read_thread_id      = this->id + "_read_thread";
        this->command_thread_id   = this->id + "_command_thread";
        this->heartbeat_thread_id = this->id + "_heartbeat_thread";
    ...

--------------------------------------------------------------------------------

![schematic](https://github.com/jpsm-at-deec/runRMP/blob/main/imgs/runRMP_drawing2.png?raw=true)

## example successful run:

![schematic](https://github.com/jpsm-at-deec/runRMP/blob/main/imgs/Screenshot_connected.png?raw=true)

![schematic](https://github.com/jpsm-at-deec/runRMP/blob/main/imgs/example.gif)





# Raspberry power supply board, ToF sensors management board, and x-bee remote control board (Made by a French robotics club)

First, we want to thank our partner JLCPCB (https://jlcpcb.com/RAT) for offering the PCBs. This was a great help to us! 

# WHO ARE WE? 
We are a French robotics club called ARFIT. Our goal is to take part in the French robotics cup each year. This year, our main project is to improve our ranking. So, for succeeding in this project, we must upgrade our robots and develop new ones. The pictures below show the competition and our robots:

![image](https://user-images.githubusercontent.com/102462067/160275075-3fe69750-3a20-4a5f-9ba8-d8582b75c5f7.png)

![image](https://user-images.githubusercontent.com/102462067/160275080-642fb2f0-372f-4e98-b9fa-7366a4cd36d0.png)
![image](https://user-images.githubusercontent.com/102462067/160275091-328efdef-3ce1-4306-8b2c-3df46469d89e.png)

In this competition, two student teams will compete. Their fully autonomous robots will have 100 seconds to earn as many points as possible. To earn points, robots must do some actions. During the 2021 edition, for instance, the robots had to move and sort green and red cups. This year, we improve our robots by making some new PCBs. Those PCBs have been manufactured by JLC PCB. Thanks to their great quality PCB and fast delivery, we were able to get to the end of our project. This article describes our PCBs, so that you will be able to reproduce them for your project. For more information on the competition please refer to:  https://www.coupederobotique.fr/

# OUR 2022 PROJECT 
This year we focused on three new PCBs. We call them the "3 ToF" board, "Raspberry pi power supply" board, and "PS2 controller with Xbee" board (ToF = Time of Flight sensors).
<ul>
  <li> The "3 ToF" board will allow us to plug 3 ToF sensors on a PCB. This board will be placed in one of our robots. With this PCB, we will have a more reliable and smaller electronic board compared to our homemade board made with a hole plate board and wires. Our new 3 ToF board will be connected to the motherboard of the robot. Those sensors will be used to detect obstacles around the robots. </li>
  <li> Thanks to the "Raspberry pi power supply" board, our raspberries pi will be supplied more easily and safely than before with a battery. This PCB will be plugged onto the raspberry pi. Then this Raspberry pi can be embedded on a robot. </li>
  <li> The "PS2 controller with Xbee" board will allow us to control robots wirelessly and with a controller. Currently, we have only one homemade board (with an Arduino UNO+a shield). During the competition, robots are autonomous but during the test, we can move them with a controller. </li>
</ul>

# GENERAL COMMENTS 
We have used KiCad v5 for designing the PCBs. First, we have made the schematics. Then we have placed the components and have traced the routes. Finally, we have created the Gerber files which can be sent to JLC PCB to manufacture the PCBs. You can find a lot of online tutorials to guide you through this process.

Once you have all the Gerber files you can go on JLC PCB Website (https://jlcpcb.com/) and upload your files. Their intuitive and efficient interface will help you to upload your files. When your files are correctly uploaded, you can click on the “order” button and select your delivery options. And … It’s done. You will receive your PCB in a few days. 

Then we bought all the required components on RS components, mouser, Pololu, Ali express... Once the parts were received, we just soldered the components in place using an iron solder and some classical tin. Again, you can find many tutorials online about how to do perfect solders.

# 3 ToF BOARD
One of our robots in development is an holonomic robot. This kind of robot can move in any direction without rotating. For detecting obstacles, our robots use Time Of Flight (ToF) sensors. On this robot, we have placed twelve of them (three on each side). These sensors must be connected to a specific hub board and then connected to the motherboard of the robot. The three sensors of one side must be connected to the hub through an HE10-10 connector already soldered on this specific hub board.

So, the easiest way that we thought was to have a PCB that have four connectors. We call this PCB: “3 ToF PCB”. Three of those connectors are used for plugging three ToF sensors. One of them (at the center) is plugged directly on the PCB and the 2 others (right and left) are connected through. The last connector on this PCB is an HE10-10 connector. So, we just need to use a ribbon cable between this PCB and the hub board. With this PCB, we have a more reliable and smaller electronic board compared to a homemade board with a hole plate board and wires. Also, we save time for finding the source of electrical problems because the connections are cleaner.

 ![image](https://user-images.githubusercontent.com/102462067/160275054-c7c0ec73-4614-41b2-8999-e4e627ce0006.png)

The schematic below is very easy. Each time-of-flight sensor (VL53L1X) communicates with the motherboard with the I²C protocol (SCl and SDA lines). Sensors are powered with 5V and GND from the motherboard. Our robot has a 4S Lipo Battery (14.8V) so we create the 5V voltage needed thanks to the D24V50F5 (Pololu Voltage Regulator). The XShut lines allow to shut down the sensors. We use these lines during the starting sequence of the robot to give a different I²C address to each sensor. This feature is handled by the hub board and the motherboard (not described here).

 ![image](https://user-images.githubusercontent.com/102462067/160275048-fad1bf24-46af-45c4-888d-5a8d56d7914e.png)

Once the schematic is done, we place the connectors, and we trace the routes. We also put two mounting holes. We simply used a two layers PCB. The bottom layer is used to make a ground plan. Do not forget to put silk-screen printing on your board!

 ![image](https://user-images.githubusercontent.com/102462067/160275042-33a2f07b-06b0-42d8-b001-7edb0e9909ba.png)

This last picture shows the robot with all 12 sensors, the robot is not finished yet. We are currently working on moving the robot:

 ![image](https://user-images.githubusercontent.com/102462067/160275039-a157c266-b0f1-403d-b195-b777ed3580fa.png)

# RASPBERRY PI POWER SUPPLY BOARD
For the years to come, we want to use one Raspberry PI by robot. Currently, we use a Raspberry only for one robot and another one on the central tracking device platform (It’s a place next to the playing field where teams can install a tracking camera). For supplying these Raspberries Pi, we used to connect two wires to +5V and GND pins of the Raspberry Pi. For improving the safety and the reliability of the connections, we decided to create a PCB that can be plugged on a Raspberry for supplying it. This board has directly a voltage regulator (+5V). So now, we have just to plug a battery into this board. This board has also some push buttons and LEDs. One of these push buttons allows us to correctly shut down the Rpi when no screen is connected. The LEDs will be used for debugging. The picture below shows the final board with the main features. 

![image](https://user-images.githubusercontent.com/102462067/160275031-eb7c04ce-d07d-44cf-9ae0-054ace37cb74.png)

We place two holes above the CPU of the Rpi to improve cooling. If needed, two fans can be mounted on the PCB to cool the system. Those fans can be supplied by a dedicated port on the PCB.

The schematic and the PCB design can be found in the picture below:
 ![image](https://user-images.githubusercontent.com/102462067/160275017-72d0aac5-8273-4619-89b7-f08633e73137.png)
 
As you can see, we also include an ADC converter for measuring the battery level. In the future we want to send this information to a supervision system. For the “power supply” connector, you can see that we place several footprints. This allows us to solder any connector we want.
![image](https://user-images.githubusercontent.com/102462067/160275015-c4974da4-eb8f-4cfe-ab5c-a8fa3d8eb5e9.png)

We design the PCB so that its size fits the size of a raspberry pi. For the smallest components, we used SMT components. For this PCB we did not use Kicad, we used Easy EDA instead. We also used LCSC to choose the components and we order an assembled PCB from JLC PCB.
 
# PS2 CONTROLLER WITH X BEE
For the French robotic cup, robots are fully autonomous but during the training, we want to control our robot with a wireless controller. 
 ![image](https://user-images.githubusercontent.com/102462067/160275006-9f6f92b0-ae29-4ce1-82ae-a6cee4a1a4a5.png)

This PCB allows us to control our robots with an old PS2 controller. When a button is pushed on the controller, the Arduino micro plugged on the PCB reads the input and sends the data to an XBee module. Another XBee is plugged on the motherboard of each robot. When a command is received the robot executes the corresponding action (move forward, rotate, …).
follow this link to find a tutorial that will give you the basics of the system: https://electropeak.com/learn/tutorial-interface-wireless-playstation-ps2-controller-arduino/
You can find our schematic and our PCB design below:

![image](https://user-images.githubusercontent.com/102462067/160274999-a7847e3c-bdad-4810-ba5d-174b053ec514.png)

 
The inputs from the PS2 controller are connected to pins of the Arduino micro according to the schematic. The device is powered by a 3S Lipo battery, therefore we used a linear voltage regulator to lower the voltage to 9V. Data are sent to the x bee through RX and TX pin. Since the Arduino and the XBee have different logic levels (5V and 3.3v), we used resistors to convert voltages. Note that the reset pin is pull High.

 ![image](https://user-images.githubusercontent.com/102462067/160274986-95921ecb-b837-4e5c-9d6e-f18b104dbf28.png)

We try to make the board as small as possible. In the future it's possible to 3D print a box for the components and the battery. We had 4 mounting holes to attach the PCB in this box.

We want to thank again JLCPCB for its support. All those PCBs were fastly delivered and correspond perfectly to our design.

<b>NB:</b> We also ordered 5 small PCBs. Those PCBs are composed of one resistor and two big pads.
 ![image](https://user-images.githubusercontent.com/102462067/160274976-9460ae08-f901-41c2-a90c-54a2c9acff85.png)

This PCB is provided by French cup staff members. It is part of one action of the book of rules. Indeed, one of the actions to make in this year’s edition is to push some wooden squares as shown in the picture below.

 ![image](https://user-images.githubusercontent.com/102462067/160274967-ab09a580-d123-40f0-8d6e-352f9e734a0f.png)

The resistance PCB is placed on top of each wooden square. There are 3 kinds of wooden squares yellow ones, purple ones, and ones with a red cross. Each kind of square has a different resistance on the top. Robots have to read the resistance on each square and push only the squares whose color corresponds to the color of their teams. For example, robots of the yellow team have to push the yellow squares, each yellow square down at the end of the match brings points to the teams. For our training, we need those resistance PCBs and JLC PCB provided them. We are again very grateful to them for this reason. 

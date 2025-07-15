 f# Hexapod
<!--- Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails! --->


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Nitya V. | Lynbrook High School | Mechanical Engineering | Incoming Junior

<!--- **Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here] (https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg) --->
# Modification Milestone 

## Description


# Final Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/wRW_JbUXg2o?si=PdZkQUoyxAZ_7aVP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<!--- For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE --->

## Description 
For my third milestone, I worked on building the remote controller for the Hexapod. The controller consists of a an acrylic plate screwed to a control board which is connected to a smart car remote shield, and a 9 volt battery holder. The remote connects to the Hexapod through two wireless modules, one placed on the Hexapod and the other placed on the remote. Once I uploaded the example sketch containing the code for the remote into the remote, and turned on power, the wireless modules allowed the Hexapod to connect to the remote. The connection between the remote and Hexapod can be verified by checking the LED3 light, which turns on when the remote and the Hexapod are connected. Once connected, you can use the joystick to control the movement of the Hexapod. There are three switches and toggles, each of which can be used for moving the Hexapod in different ways, like moving straight, turning, and rotating in place. There are also 2 knobs, which can be used to change the Hexapod's height, or rotate the robot in place. When the joystick is pressed, the Hexapod also switches between sleep mode and active mode. The Hexapod also has a built-in feature that puts it in sleep mode everytime no commands are issued for 10 seconds. 

<!--- #### Figure  - Schematic of Robot Controller 
--->

### How it Works - Wireless Module 

![Wireless Module](wireless_module_photo.svg)

The wireless modules allow wireless communication between the control board in the Hexapod and the control board in the remote controller. The wireless module contains a tranceiver, which works as both a transmitter and a receiver, and an antenna, which transmits and receives radio waves. The wireless module uses an SPI interface to create a connection between the module and their microcontroller baords. There are 6 SPI pins: the Master Out Slave In (MOSI) pin, the Master In Slave Out (MISO) pin, the serial clock pin (SCK), the chip enable (CE) pin, the chip select not (CSN) pin, and the IRQ pin. The MOSI pin transmits data from the master, the board, to a slave, which is the module in this case. The MISO pin transmits data from the slave, the module, to the master, the board. The SCK pin helps coordinate the timing of the data transfer, and maintains a steady frequency in the clock signal. The CE pin is responsible for activating and deactiving the chip (module). This is important when controlling multiple chips on a board and choosing which chip is communicating with the board, and is also useful in reducing power consumption when a chip doesn't need to communicate with the board. The CSN pin is used to turn the communication with the board on and off. The IRQ pin indicates when data has been sent or recieved, triggering the interrupt on the microcontroller. The other two pins are GND, ground, and VCC (3V), power. 

## Challenges
When I first tried uploading the example sketch into the remote, I kept getting an error and the Arduino IDE failed to recognize my board. Initially, I tried to restart the Arduino IDE and my computer, but I kept getting the same error. Eventually, I was able to upload the sketch into my remote without an error, with the help of an instructor who had to change the address of the board in the arduino config files. 

## Next Steps 
 Next, I will work on my modifications. My first modification will be to add ultrasonic sensors to the front and back of my Hexapod so that it can move by itself and avoid obstacles by detecting them with the ultrasonic distance sensors. 

# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/f6aHOOFBFAY?si=haOz7Pi0kzS1B6U4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 

<!--- For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you over
- What needs to be completed before your final milestone --->


## Description 
Next, I worked on calibrating and controlling the movement of my Hexapod through the Processing App. To calibrate my robot, I had to connect it to the processing app to put it into calibration mode, and then use the Processing App to individually move each leg of the Hexapod to match its position on the calibration graph. Now that I have calibrated the robot, everytime I connect it to power, it will automatically go into its default position. Once I calibrated the Hexapod, I could control its movement through the Processing App. All the code for the Hexapod's movement came from the original example sketch I uploaded into the Hexapod. I can also wirelessly connect the Hexapod to the Processing App, because of the WLAN module, which creates a Wi-Fi I can connect my computer to. Once connected to the Wi-Fi, the Processing App can wirelessly connect to the Hexapod, so I can control its movement and give it basic movement commands.  

### How it Works - Calibration 
The purpose of calibrating the Hexapod is to set its default position when power is turned on. When the calibration is confirmed in the Processing App, the data is stored in the robot. The code below is a snippet of the code from the Processing App library that creates the Processing Sketch that can be used to control the Hexapod when connected. 

```
 // tab Calibration
    // move leg
    case(402): //checks if the id value matches 402 
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), 0, dL, 0); // moves leg 1 mm in the positive  y dimension 
    break;  //stops running code for this case
    case(403):
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), 0, -dL, 0); //moves leg 1 mm in the negative y dimension 
    break;
    case(404):
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), dL, 0, 0);  //moves leg 1 mm in the positive x dimension
    break;
    case(405):
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), -dL, 0, 0); //moves leg 1mm in the negative x dimension
    break;
    case(406):
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), 0, 0, dL); //moves leg 1 mm in the positive z dimension
    break;
    case(407):
    controlRobot.MoveLeg((int)(cp5.getGroup("radioButton2").getValue()), 0, 0, -dL); //moves leg 1 mm in the negative z dimension
    break;
    // calibrate
    case(408):
    controlRobot.Calibrate();
    break;
    case(409):
    controlRobot.CalibrateState();
    cp5.getController("confirm").unlock();
    cp5.getController("confirm").setColorLabel(255);
    break;
    case(410):
    controlRobot.CalibrateVerify();
    cp5.getController("confirm").lock();
    cp5.getController("confirm").setColorLabel(160);
    break;
  }
}
```

#### Figure - Processing Sketch Calibration Tab

![Processing Sketch Calibration Tab](calibration_tab.png)


#### Figure  - Calibration Graph

This is the graph the legs of the Hexapod are aligned with, for the default position.

![Calibration Graph](CalibrationGraph_for_V3.pdf)

## Challenges 
At first, I faced a lot of challenges while calibrating my Hexapod because my robot struggled to hold its position and sometimes would just stop moving. I then realized I had screwed on the white disks that held the servos in place backwards. Because of the lack of support, holding the part of the servos that acted as the hinges for the legs, the legs of my Hexapod kept flopping down instead of holding their position. When I fixed the placement of the white disks and screwed everything back on correctly, the servos were able to hold their position and I could easily calibrate the Hexapod. When correctly screwed on, the servos make a buzzing sound while moved, and cannot be manually moved when power is turned on. 

## Next Steps 
For my third milestone, I will work on creating the remote controller and controlling the Hexapod through the controller. The remote controller can wirelessly connect to the Hexapod, so once the controller is made, I will be able to move my Hexapod without connecting it to my computer or the Processing App. 

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/rb6JfESJuJA?si=rGa8E70MRsebYPxD&amp;controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 

## Description

My project is the Hexapod, a six-legged robot which can be controlled by a controller. It consists of a control board connected to 18 servos with black acrylic plates. In my first milestone, I assembled the body and legs of the Hexapod. I first uploaded a default example sketch into my control board and connected the control board to the Processing App using a USB cable to make sure my batteries were at the correct voltage, around 8 volts, and that my servos were all working properly. I installed the batteries into the control board by connecting screwing in the metal part of a pair of female wires, and turned power on by connecting the female wires with the pair of male wires attatched to the pack of batteries. To test my servos, I had to plug them into pins 22-39 in the back of the control board and make sure all the wires of the servos were placed correctly. I then joined the bottom acrylic plate to the control board, the servos, and the acrylic legs of the robot using screws, nuts, and brass standoffs. This part took me a lot of time because I had to play close attention to the orientation of the servos and legs, and the screws were also really small and kept on slipping from my hands. While screwing in the servos, I had to keep the control board in installation mode (the mode is changed in the Processing sketch) and make sure the board was connected to power.  After successfully connecting the legs to the main acrylic plate, I had to rewire all the servos in the correct pins so that all the servos would be able to move freely later. After correcting the wiring I also used a cable tidy to make the wires as neat as possible. Finally, I attatched the WLAN module, a small chip, to the control board. The WLAN module, similar to Wi-Fi, alllows Hexapod to wirelessly connect and be controlled by the Processing App. 


## Challenges

I mainly faced challenges while screwing together different parts, because I had to play attention to detail to the orientation of parts and how to screw them. I often had to  unscrew and re-screw parts because of this. I also had trouble uploading the default sketch into the control board and Arduino kept giving me an error, but with some help from instructors I learned to debug errors and realized I was using the wrong board. 

## Next Steps 

My next steps are to work on calibrating my robot and building the controller. 


 Figure 2 - Schematic of Hexapod 
 ![schematic of control board](circuit.svg.svg)


# Starter Project Milestone - Weevil Eye

<iframe width="560" height="315" src="https://www.youtube.com/embed/MTQ2BYpMcPU?si=rvORzKBOlAVMeMWE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Description

My starter project was the Weevil Eye. I chose this project because I wanted to work on my soldering skills. The Weevil Eye consists of a board connected and soldered to a transistors, three resistors, a photoresistor and 2 LED lights, and it is in the shape of a bug with six legs. when a battery is attatched to battery clip on the bottom of the board, the LED lights (the eyes of the bug) light up. I learned a lot through this project, like how solder conducts electricity and the importance of soldering correctly to avoid any mishaps in the current flow. I also had to make sure to correctly orient the polarized LED lights and make sure both the positive sides and btoh the negatives went together.

## Challenges

At first, when I put the battery into the clip at the bottom of the board, the LED lights did not light up, so I had to troubleshoot to see if there were any problems with my soldering. I did not notice any, and also saw that the LED lights lit up for a short second when I was fixing different components. With a bit of help from my instructor, I realized that the LED lights lit up when I lightly pressed the main photoresistor on the the board, the LED lights did light up. This was because the photoresistor is sensitive to light, and only allows the LED lights to light up when it doesn't sense light. When the resistor was slightly pressed, reistance got reduced and current flowed through the LED lights, making them light up.

## Next Steps

My next steps are to start working on my main project, the Hexapod.


<!--- # Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
--->

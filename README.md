Download Link: https://assignmentchef.com/product/solved-ee371-lab-1-parking-lot-occupancy-counter
<br>
This lab is a refresher to the finite state machines that you learned in EE 271 by designing a parking lot occupancy counter.

Laboratory Design Kits

We will use the DE1-SoC development board that you used in EE 271. Please pick up your lab kit from the EE store.

Using Quartus II Software

The Quartus II web edition release 17.0 is preloaded on the machines in the department, and you can do all the work on these PCs. However, if you have a PC of your own that you would like to use, you can install the software for free. To install the software, go to

<u><a href="http://fpgasoftware.intel.com/17.0/?edition=lite&amp;platform=windows&amp;download_manager=dlm3%20">http://fpgasoftware.intel.com/17.0/?edition=lite&amp;platform=windows&amp;download_manager=dlm3 </a></u><a href="http://fpgasoftware.intel.com/17.0/?edition=lite&amp;platform=windows&amp;download_manager=dlm3%20">,</a> <strong>choose version 17.0 from the top drop-down menu</strong>, download the free web edition and install it. Note that you will have to register to be able to download the software. The file to download is the 5.8 GB tar file under the “Combined files” tab. Extract the tar file using a program like 7-zip and run the QuartusLiteSetup17.0-windows.exe file. When it asks for the components to install, make sure you select each of these:

Quartus Prime Lite Edition (Free)

Devices: Cyclone V

ModelSim: Intel FPGA Starter Edition (Free)




When the software is done, make sure to install the USBblaster driver. Run Quartus next, and if asked about licensing just run the software (we use the free version, so no license required).




<strong>NOTE</strong>: If you have trouble accessing the website to download the software, you can download it from this google drive. (you need to login using your netID)

<u><a href="https://drive.google.com/open?id=1Tl_1G_DFn6Yps0DuEh3yUAr4vXpJ48SF">https://drive.google.com/open?id=1Tl_1G_DFn6Yps0DuEh3yUAr4vXpJ48SF</a></u>

Task 0: Warm up exercise on Quartus and ModelSim




<strong><em>This task is a refresher on creating a Quartus project, writing a SystemVerilog program and simulating it in ModelSim. You can skip this task if you do not need a refresher.  </em></strong>




For this task, follow along a series of video tutorials that will walk you through the steps of creating a full adder using SystemVerilog and simulating the design in ModelSim. For your reference, the source code used in the tutorials is in the appendix of this document.




Please follow the tutorials in the following order:




<ol>

 <li>Launch the Quartus Prime software.</li>

 <li>Create a project from scratch. Please follow the steps in the following videos and use the same project name as in the video</li>

</ol>

<u><a href="https://youtu.be/iLbmSTG7bpA">https://youtu.be/iLbmSTG7bpA</a></u>




<ol start="3">

 <li>Implement the full adder using SystemVerilog and simulate it using ModelSim. Please follow the following video: <em>Please note that in the video when it refers to compiling the project for the first time, it may give you a compilation error. If you run the video for few more seconds it’ll tell you about setting the top level modules so that the program compiles</em>. <u><a href="https://youtu.be/BcvclrqZ2fc">https://youtu.be/BcvclrqZ2fc</a></u></li>

</ol>




<ol start="3">

 <li>Mapping a SystemVerilog design to an FPGA. <u>https://youtu.be/mnZt2iNNfp4</u></li>

</ol>




<ol start="5">

 <li>Loading the design onto the FPGA. Please follow the steps in the following video and test your full adder on the DE1_SoC board and verify that it matches the truth table. <u><a href="https://youtu.be/uMxA3VcS3f8">https://youtu.be/uMxA3VcS3f8</a></u></li>

</ol>







After completing this task, you should create future projects in a similar fashion and use SystemVerilog and ModelSim accordingly.

<strong> </strong>

<strong> </strong>

<h1>Assigned Task</h1>







<h2>Parking Lot Occupancy Counter</h2>

<strong> </strong>

Consider a parking lot with a single entry and exit gate. Two pairs of photo sensors are used to monitor the activity of cars, as shown in Figure 1. When an object is between the photo transmitter and the photo receiver, the light is blocked, and the corresponding output is asserted to 1.  By monitoring the events of two sensors, we can determine whether a car is entering or exiting, or a pedestrian is passing through. For example, the following sequence indicates that a car enters the lot:




<ul>

 <li>Initially, both sensors are unblocked (i.e., the a and b signals are “00”).</li>

 <li>Sensor a is blocked (i.e., the a and b signals are “10″).</li>

 <li>Both sensors are blocked (i.e., the a and b signals are “11”).</li>

 <li>Sensor a is unblocked (i.e., the a and b signals are “01”).</li>

 <li>Both sensors become unblocked (i.e., the a and b signals are “00”).</li>

</ul>







<em>Figure 1 Parking lot sensors </em>




Design a parking lot occupancy counter as follows:

<ol>

 <li>Design an FSM with two input signals, a and b, and two output signals, <em>enter</em> and <em>exit</em>. The <em>enter</em> and <em>exit</em> signals assert true for one clock cycle when a car or exits the lot, respectively. Derive the SystemVerilog code for the FSM and simulate it in ModelSim. You may assume that cars will not change direction while entering or exiting the parking lot.</li>

 <li>Design a counter with two control signals, <em>inc</em> and <em>dec</em>, which increment and decrement the counter when asserted. Assume that the maximum capacity of the parking lot is 25 spots. Derive the SystemVerilog code for the FSM and simulate it in ModelSim.</li>

 <li>Combine the counter and the FSM and model the parking lot, using push buttons to mimic the two sensor outputs and the seven-segment displays to display the car count. Your system should have the following:

  <ol>

   <li>Display the car counts as they enter the parking lot on the seven-segment displays HEX0 and HEX1.</li>

   <li>If the counter reaches 25, display the word “FULL” on HEX5-HEX2</li>

   <li>As cars exit the lot, the counter decrements and the corresponding number should be displayed on HEX0 and HEX1.</li>

   <li>When the lot is empty. Display the word “EMPTY” on HEX5-HEX1 and display the number ‘0’ on HEX0.</li>

   <li>Use 2 off-board LEDs to represent the a and b signals. When a is 1, turn on a red LED, and when a is 0, turn off a red LED. Stimulatingly, when b is 1, turn on a green LED, and when b is 0, turn off a green LED.</li>

  </ol></li>

 <li>Simulate the system in ModelSim.</li>

 <li>Download the program to the DE1_SoC board and demonstrate it to your TA.</li>

 <li>Create a block diagram for your system and include it in your lab report.</li>

</ol>






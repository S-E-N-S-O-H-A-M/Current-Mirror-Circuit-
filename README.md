# Design of a Current Mirror Circuit in 130 nm CMOS Technology
<p>Readme.txt presents process of design and simulation of a CMOS Current Mirror circuit using esim and sky130 technology.The specifications of the design can be found here.</p>
<p>---------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Table Of Contents</p>
<p>(1)Circuit Details</p>
<p>(2)Tools</p>
<p>(3)Circuit Design</p>
<p>(4)Circuit Simulation</p>
<p>(5)Observation</p>
<p>(6)Contributor</p>
<p>(7)Acknowledgement</p>
<p>---------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Circuit Details</p>
<p>The Current Mirror Circuit is a popular technique for monolithic IC design. The circuit is designed in a way such that it copies the current through one active device to a different active device with a current control feature. In this, the current flowing through one device is copied into another device but in inverting form. If the current of the primary device is modified, the mirrored current output of the opposite device also will change. So by controlling the current in one device, the current in another device also can be controlled. Thus the current mirror circuit is usually mentioned as a Current Controlled Current Source or CCCS. This current mirror circuit can be implemented with two PMOS transistors. In Figure 1, the two NMOS transistors are considered M1 and M2. An NMOS is always operating in the saturation region when the drain is shorted to its gate, as shown in Figure 1. In this case, Vds is equal to Vgs which is greater than Vth subtracted from Vgs implying saturation always where Vgs is the gate to source voltage, Vth is the threshold voltage, Vds is a drain to source voltage. Thus the first NMOS i.e. M1 is in the saturation region whereas the second NMOS i.e. M2 is in the saturation region if the output voltage is higher than the saturation voltage. Therefore the input current of the first NMOS can control the output current of the second NMOS. Hence the output current can be mirrored like the input current, Iout is equal to Iref.</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Tools</p>
<p>The tools used for circuit design and simulations are:</p>
<p>(1)eSim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>(1.1)Steps to download and install esim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.1) Download the latest eSim release for Windows OS from the link: https://esim.fossee.in/downloads .</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.2) Locate the installer file in the folder where your downloaded files are kept.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.3)Double click on the file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.4) If a pop-up window appears asking &quot;Do you want to allow the following program from an unknown publisher to make changes <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>to this computer?&quot;,click YES.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.5)Then in the &quot;License Agreement&quot; window, select the I Agree option.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.6). Click Next when the program asks for you to &rdquo;Choose Install Location&rdquo;.We have taken care to auto-select the destination <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>folder path.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.7)In the next window that appears, select Install.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.8)A progress bar will appear; once it reaches 100%, &quot;Installation Complete&quot; message will be shown at the top of the eSim <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>setup window. Click on Close. eSim shortcut icon will be on your Desktop.</p>
<p><br></p>
<p>(2)SkyWater SKY130 PDK</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>(2.1)Steps to download</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2.1.1)Download using this link and unzip: https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip</p>
<p>(3)ngspice</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>It is already installed with esim.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span></p>
<p>The schematics for Current Mirror Circuit was designed in eSim and simulated in ngspice.</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Circuit Design</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>--&gt;Steps:</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1)Design the crcuit in esim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2)Genreate the netlist in esim&nbsp;</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(3)Open the workspace folder where esim projects are saved. Open the &quot;Current_Mirror&quot; folder.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(4)Copy the .cir.out file and save in the sky_fd_pr folder downloaded earlier as .cir file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(5)Open with notepad and add the path .lib &quot;models/sky130.lib.spice&quot; tt at the top.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(6)Replace with CMOSP, mos_p with sky130_fd_pr__pfet_01v8 and CMOSN, mos_n with &nbsp;sky130_fd_pr__nfet_01v8.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(7) To replace inductor, capacitor, resistor do it this way for example: L1 out gnd 1m by x1 &nbsp;out gnd mid 0 sky130_fd_pr__ind_03_90.</p>
<p>Note: For more details go to the cells folder in sky_fd_pr. Open the specific component folder which you want to use. Then open the test folder and check the SPICE file. The SPICE file is an example of implementation of that component. You will get to know how to use the component in your ckt.</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Circuit Simulation</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>--&gt;Steps:</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1)Right click on .cir file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2)Click on Open With</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(3)Browse for the ngspice.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(4)If ngspice not present scroll down click on More Apps.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(5)Go to the FOSSEE folder search for Ngspice. Run it</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Observation</p>
<p>The input current is equal to the magnitude of output current.The output current is in negative because current is flowing in opposite direction.</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Contributor</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>-Soham Sen, B.Tech (Electronics and Communication Engineering), Amity University Kolkata - sohamsen25420001@gmail.com</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>

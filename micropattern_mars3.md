# Micropatterning of thin films using a SLA 3D Printer 

### in collaboration with Mayuran Saravanapavanantham

Goal of this first set of experiments is to show whether we can use an SLA 3D to micropattern a film of photoresist spin-coated onto a Silicon wafer. This step is the starting point of every photolithography process. This approach is analogous to classic flood-expose through a photomask, except in this approach the photomask is digitally created from a CAD file and not a physically manufactured part that makes rapid prototyping impossible and redesigns costly and slow. Direct-write lithography tools like the Heidelberg MLA150 exist for flexible designs but are both very expensive (~100,000s USD) and comparably slow, especially for larger area (up to 6 inch) exposures due to the nature of tracing out the input pattern.  

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/Elegoo_Mars3_printer.png" width="20%" />

Here, we use a 350$ SLA 3D printer, the Elegoo Mars 3, to expose our pattern created in Fusion360 and exported as an STL file. The Elegoo Mars features a 4K 6.6 inch LCD with 4098\*2560 pixels to project an image from a 405nm UV backlight. This yields a pixel-limited resolution of 35 um. While this rival the sub-1-micron resolution of the MLA150, a lithography process using this as an expsosure method may enable micron-scale precision patterning in hobbyist-spaces by being both cheap and space-efficient. Possible fields of applicationa where the here obtained resolution is sufficient are MEMS fabrication, Lab-on-a-chip/Microfluidics, as well as rapid prototyping of tiny and flexible PCBs, but also waveguides, metasurfaces, microanteannas and much more.

## Sample Preparation

### Sample cleaning

Sample cleaning was carried out in the Baldo lab by sonicating 1x1 inch samples of cleaved single crystal Silicon in acetone and IPA for 2 minutes each, followed by blow-drying with nitrogen. 

### Spin-Coating

The resist used here is [AZ3312](https://cores.research.asu.edu/sites/default/files/2019-10/az_3312_photoresist_data.pdf) is the standard positive photoresist provided by MIT.nano.  
The resist was spin-coated in the Class 100 cleanroom area within MIT.nano. A Class 100 Cleanroom contains less than 100 particles larger than 0.5 microns per cubic foot of air. A near-particle-free environment is of utmost importance for a high result yield in micro-fabrication, as dust particles settling on the surface will cause defects in structures created by patterned photoresist on the substrate surface. The AZ3312 was spin-coated at 3000 rpm for 60 seconds onto the Silicon wafers after a 5 min substrate-drying bake step, which improves resist adhesion.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3788.JPEG" width="30%" />

After resist spinning of soft-bake step was carried out for 90 seconds at 100 C.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3791.jpeg" width="30%" />

## Measurement of Lamp Intensity and Calculation of UV exposure time

The required UV exposure dose can be found in the data-sheet linked above to be 100 mJ/cm2. AZ3312 can be exposed both at i-line at h-line, meaning 365 nm wavelength and 405 nm, respectively.  
In order to determine the correct exposure time, the lamp intensity must be known. For this we used a calibrated Si-photodiode from [Thorlabs](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=2822) which was placed face down directly on the glass panel of the Elegoo Mars 3. In complete darkness, UV exposure of the photodiode yielded a detected current of 150 uA. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3785.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3787.JPEG" width="30%" />

Knowing that the 3D printer's lamp is a 405 nm UV lamp, the diode sensitivity can be read out from the calibration data to be 0.065 A/W. Dividing the detected current by the sensitivity value yields a lamp irradiance of 2 mW. Since the area of the photodiode is 1x1 cm, the UV-light intensity is thus 2 mW/cm2. To finally obtain the required exposure time from this, one simply needs to divide the exposure dose by the lamp intensity, yielding an exposure time of *50 seconds*. 

## CAD of test structures to pattern into resist

Structures for two experiments to be carried out were designed in Fusion 360, as expounded below. Test structures chosen here were sets of square pads of varying size and spacing as well as a continuous trace of increasingly lower width.  

Since in an SLA 3D printer the bodies in the STL file are usually the areas of the resin to be hardened, *solid bodies will be exposed areas on the printer bed*. As AZ3312 is a positive resist, exposed areas in the polymer are broken down and will be washed away in the developer. Thus, in the case of the bodies shown in the first image below, the pads and lines will wash away while all other resist on the substrate remains in place. From an adhesion perspective, it is evidently a lot easier to develop structures in a matrix of connected resist than vice versa. 

Sizes of the structures designed below range from 5 mm down to 10 um side length for the pairs of square pads. The smallest pads are not expected to be possible to develop with this approach since their side length is below the pixel resolution of the printer. Equivalently, the connected lines on the right-hand side range from 500 um to 25 um line width.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/CAD_pads_lines.png" width="30%" />

In order to create free-standing structures I inverted the above patterns such that the structures to leave behind are cut-outs in a solid body. Thus, all resist surrounding the pads and lines will be exposed. The resulting body is shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/CAD_pads_lines_inverted.png" width="30%" />

The exported STL files were then exported and sliced in the CHITUBOX software recommended by Elegoo for use with their 3D printers. The height of the bodies to pattern is arbirtary here as we simply set the bottom layer exposure time to the exposure time calculated above and stop the print after the bottom layer exposure is complete.

## UV-exposure on Elegoo Mars 3 printer

UV exposure was carried out by placing the resist-coated wafer upside down directly on the glass panel of the printer's LCD screen, as shown below. Exposure, as mentioned above, was set by the bottom layer exposure time parameter in CHITUBOX.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3794.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3795.JPEG" width="30%" />

## Resist development

The resist was developed in MIT.nano in AZ300 MIF Developer for 90 seconds at room temperature.

## 1st experiment: Develop structures in a matrix of undeveloped resist

Here, the first design file shown above of individual bodies of pads and lines was used. Thus, the resist inside those structures was exposed and subsequently developed away, leaving the surrounding matrix of photoresist intact.

A photo of the sample after resist development is shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3808.JPEG" width="30%" />

### Characterization in Optical Microscope

All following images were taken at 5x magnification.

The image below shows 200 um pads on the very left down to 10 um pads on the very right. A seen in the image pads of 50 um side length and gap cannot be resolved cleanly anymore. Further, note the singular dust particle creating a significant defect in one of the 200 um pads, highlighting the importance of a low-particle environment.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/5x_small_pads_annotated.png" width="30%" />

Notable in the image above is the partly developed border region between exposed and unexposed areas. The width of these poorly defined border regions is very close to 35 microns, matching exactly the pixel size of the display. An explanation for that may be that may be that liquid crystals adjacent in on/off position require 1 pixel in between that let's part of the ligth pass, as indicated in the schematic below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/border_liquid_crystal_alignment.png" width="20%" />

Investigating the developed line patterns, the image below shows the tranisition of the 500 um trace to the 200 um trace. Interestingly, the cleanly developed region inside the trace is close to 250 um wide where it is defined to be 200 um wide in the CAD file. Further the above mentioned partly-exposed border region is clearly visible here and measuring 35 um width as well. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/5x_200um_500um_annotated.png" width="30%" />

Due to these poorly exposed border regions the 50 um and 25 um trace widths are not well developed, as shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/Img4-5x_25um_50um_annotated.png" width="30%" />

A solution for this issue of ill-defined border regions could be overexposure of the resist. This should yield a cleaner edge, as the above partly-exposed pixels should develop away with sufficient exposure. This approach will be explored in the second experiment described below.

## 2nd experiment: Develop free-standing resist structures with improved edges by resist over-exposure

The goals of the second experiment were to 1) determine the scale down to which free-standing structures can be created with this approach (key e.g. for PCB fab), and 2) test whether the border regions between exposed and unexposed areas can be improved by resist over-exposure.  
For the over-exposure I at random picked a more than doubled exposure time by setting it to *120 seconds*.  

The Si substrate with the developed free-standing pads and lines is depicted below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3885.JPEG" width="30%" />

### Characterization in Optical Microscope

As above, all images were taken at 5x magnification.

First, we can see that the over-exposure had the desired effect. Both the 500 um pad and line, shown below, are almost exactly 70 um thinner than in the CAD file, meaning that on each border one extra line of pixels was, as intended, developed away and left behind a clean line. Thus, this has to be taken into account in the design process, making structures 70 um wider than desired in the final product.  
Notable here is that interestingly there is an anisotropy between the x- and y-axis in cleanliness of exposure. From a hardware perspective this would not be expected, as the spacing of the pixel matrix should be identical in both axis. This makes the driving software being the cause a likely explanation.  
However, this effect can presumably be mitigated or eliminated by fine-tuning the over-exposure, performing an exposure array between 50 seconds and 120 seconds in order to find the optimum.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_pad_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_200um_line_annotated.png" width="30%" />

The anisotropy is also very clearly visible in the smaller, especially square, structures, as shown below. For both the pads and the lines structures are missing an additional 10-15 um in width, and a second row of partly exposed pixels seems to partly expose the resist in that direction. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_pad_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_line_annotated.png" width="30%" />

As depicted below, the 200 um line ends abruptly meaning that the 100 um (in design file) and below lines fully washed away. Equivalently, the 200 um pads shown above, yielding 115-135 um large pads in reality, were the smallest ones to remain undeveloped on the surface.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_100um_line.png" width="30%" />

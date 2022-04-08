# Micropatterning of Thin Films Using an SLA 3D Printer 

### in collaboration with Mayuran Saravanapavanantham

<br />

## Introduction to Experimental Approach

Goal of the below described first set of experiments is to show whether we can use an SLA 3D printer to micropattern a film of photoresist spin-coated onto a Silicon wafer, that is, to perform a cheap and easy basic photolithography process. This approach is analogous to the classic lithographic flood-expose through a photomask, (tool cost on the order of 100,000 USD). The big difference here being that the exposure tool cost less than 500 USD and the photomask is digitally created from a CAD file, not a physically manufactured part making rapid prototyping impossible and redesigns costly and slow. Direct-write lithography tools like the Heidelberg [MLA150](https://heidelberg-instruments.com/product/mla150/) exist for flexibility in patterning directly from digital designs but are both very expensive (> 200,000 USD), large tools and comparably slow, exposures due to the nature of the approach of physically tracing out an input pattern to expose.  

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/Elegoo_Mars3_printer.png" width="20%" />

Here, we use a 350$ SLA 3D printer, the Elegoo Mars 3, to expose our structures created in Fusion 360 and exported as STL files. The Elegoo Mars features a 4K 6.6 inch LCD with 4098\*2560 pixels to project an image from a 405nm UV backlight. This yields a pixel-limited resolution of 35 um. While this does not rival the 1-micron resolution of the MLA150, a lithographic process using the LCD projection approach tested here, may enable micron-scale precision patterning in hobbyist-spaces by being both very cheap and a space-efficient tabletop solution. Possible fields of applications may be, bot not limited to, **MEMS fabrication, Lab-on-a-chip/Microfluidics, as well as rapid prototyping of tiny and flexible PCBs**, but also waveguides, metasurfaces, microanteannas and many more.

## Sample Preparation

### Sample Cleaning

Sample cleaning was carried out in the Baldo lab by sonicating 1x1 inch samples of cleaved single crystal Silicon substrates in acetone and IPA for 2 minutes each, followed by blow-drying with nitrogen. 

### Spin-Coating

The resist used here for a first test is [AZ3312](https://cores.research.asu.edu/sites/default/files/2019-10/az_3312_photoresist_data.pdf) and is the standard positive photoresist provided by MIT.nano.  
The resist was spin-coated in the Class 100 cleanroom area within MIT.nano. A Class 100 Cleanroom contains less than 100 particles larger than 0.5 microns per cubic foot of air. A near-particle-free environment is of utmost importance for a high result yield in micro-fabrication, as dust particles settling on the surface will cause defects in structures created by patterned photoresist on the substrate surface.  
The AZ3312 was spin-coated at 3000 rpm for 60 seconds onto the Silicon wafers after a 5 min substrate-drying bake step to improve resist adhesion.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3788.JPEG" width="30%" />

After resist spinning a soft-bake step was carried out at 100 C for 90 seconds.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3791.jpeg" width="30%" />

## Measurement of Lamp Intensity and Calculation of UV Exposure Time

The required UV exposure dose can be found in the data-sheet linked above to be 100 mJ/cm2. AZ3312 can be exposed both at i-line at h-line, meaning 365 nm wavelength and 405 nm, respectively.  
In order to calculate the correct exposure time, the lamp intensity must be known. To determine this we used a calibrated Si-photodiode from [Thorlabs](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=2822) which was placed face down directly on the glass panel of the Elegoo Mars 3. In complete darkness, UV exposure yielded a detected current of 150 uA flowing through the photodiode. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3785.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3787.JPEG" width="30%" />

Knowing that the 3D printer's lamp is a 405 nm UV lamp, the diode sensitivity can be read out from the calibration data to be 0.065 A/W. Dividing the detected current by the sensitivity value yields a lamp irradiance of 2 mW. Since the area of the photodiode is 1x1 cm, the UV-light intensity is thus 2 mW/cm2. To finally obtain the required exposure time from this, one simply needs to divide the exposure dose by the lamp intensity, yielding an exposure time of *only 50 seconds*. 

## CAD of test structures to pattern into resist

Structures for two experiments to be carried out were designed in Fusion 360, as expounded below. Test structures chosen here were sets of square pads of varying size and spacing as well as a continuous trace of increasingly lower width.  

Since in an SLA 3D printer the bodies in the STL file are usually the areas of the resin to be hardened, *solid bodies will be exposed areas on the printer bed*. As AZ3312 is a positive resist, exposed areas in the polymer are broken down and will be washed away in the developer. Thus, in the case of the bodies shown in the first image below, the pads and lines will wash away while all other resist on the substrate remains in place. From an adhesion perspective, it is evidently a lot easier to develop structures in a matrix of connected resist than vice versa. 

Sizes of the structures designed below range from 5 mm down to 10 um side length for the pairs of square pads. The smallest pads are not expected to be possible to develop with this approach since their side length is below the pixel resolution of the printer. Equivalently, the connected lines on the right-hand side range from 500 um to 25 um line width, that is, trace widths of about 20 mils down to 1 mil.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/CAD_pads_lines.png" width="30%" />

In order to create the opposite, free-standing structures in resist, I inverted the above patterns such that the structures to leave behind are cut-outs in a solid body. Thus, all resist surrounding the pads and lines will be exposed. The resulting body in the CAD file is shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/CAD_pads_lines_inverted.png" width="30%" />

The exported STL files were then sliced and prepared for print in the [CHITUBOX](https://www.chitubox.com/en/index) software recommended by Elegoo for use with their 3D printers. The height of the bodies to pattern is arbirtary here as we simply set the bottom layer exposure time to the exposure time calculated above and stop the print after the bottom layer exposure is complete.

## UV-exposure on Elegoo Mars 3 printer

UV exposure was carried out by placing the resist-coated wafer upside down directly on the glass panel of the printer's LCD screen, as shown below. The correct exposure time, as mentioned above, was set by the bottom layer exposure time parameter in CHITUBOX.

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

Notable in the image above is the partly developed border region between exposed and unexposed areas. The width of these poorly defined border regions is very close to 35 microns, matching exactly the pixel size of the display. An explanation for this may be that liquid crystals adjacent to each other in on/off position always have one pixel in between them that is only partly closed, as indicated schematically below, thus resulting in a single pixel line of under-exposure.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/border_liquid_crystal_alignment.png" width="20%" />

Investigating the developed line patterns, the image below shows the tranisition of the 500 um trace to the 200 um trace. Interestingly, the cleanly developed region inside the trace is close to 250 um wide where it is defined to be 200 um wide in the CAD file. Further the above mentioned partly-exposed border region is clearly visible here, too, and measuring 35 um in width. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/5x_200um_500um_annotated.png" width="30%" />

Due to these poorly exposed border regions the 50 um and 25 um trace widths are not well developed, as shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/Img4-5x_25um_50um_annotated.png" width="30%" />

A solution for this issue of ill-defined border regions could be over-exposure of the resist. This should yield a cleaner edge, as the above partly-exposed pixels should develop away with sufficient exposure. This approach will be explored in the second experiment described below.

## 2nd experiment: Free-standing resist structures with improved edges by resist over-exposure

The goals of the second experiment were to 1) determine the scale down to which free-standing structures can be created with this approach (key e.g. for PCB fab), and 2) test whether the border regions between exposed and unexposed areas can be improved by resist over-exposure.  

For the over-exposure I, at random, picked a more than doubled exposure time setting it to *120 seconds*.  

The Si substrate with the developed free-standing pads and lines is depicted below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3885.JPEG" width="30%" />

### Characterization in Optical Microscope

As above, all images were taken at 5x magnification.

First, we can see that the over-exposure had the desired effect. Both the 500 um pad and line, shown below, are almost exactly 70 um less wide than designed in the CAD file, meaning that on each border one extra line of pixels was, as intended, developed away and left behind a clean line. Thus, this has to be taken into account in the design process, making structures 70 um wider than desired in the final product.  
Notable here is that interestingly there is an anisotropy between the x- and y-axis in cleanliness of exposure. From a hardware perspective this would not be expected, as the spacing of the pixel matrix should be identical in both axes. Hence, the pixel-driving software being the cause of this may be a more likely explanation.  

In any case, this effect can presumably be mitigated or eliminated by fine-tuning the over-exposure, performing an exposure array between 50 seconds and 120 seconds in order to find the optimum.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_pad_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_200um_line_annotated.png" width="30%" />

The anisotropy is also very clearly visible in the smaller, especially square, structures, as shown below. On the y-axis both the pads and line structures are missing an additional 10-15 um in width, and a second row of partly exposed pixels seems to be present in that direction, too. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_pad_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_line_annotated.png" width="30%" />

Last, as depicted below, the 200 um line ends abruptly meaning that the 100 um (in design file) and below lines fully washed away. Equivalently, the 200 um pads shown above, yielding 115-135 um large pads in reality, were the smallest ones to remain undeveloped on the surface.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_100um_line.png" width="30%" />

## Next Steps

The next steps on this project will be:
1. Fine-tuning the exposure dose to find the lower size limit of free-standing structures that can be created using AZ3312.
2. Experiment with adhesion promoters and/or other resists to lower the size limit. For example SU-8 negative resist is very commonly used in microfluidics fabrication and is known to have excellent adhesion to many substrates.
3. Try spin-coating resist on FR-1 substrates and attempt to transfer the pattern into the copper clad by wet-etch. The areas masked by resist are protected here, thus, traces for PCB manufacturing may be created this way.

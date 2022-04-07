# Micropatterning of thin films using a SLA 3D Printer 

### in collaboration with Mayuran Saravanapavanantham

Goal of this first set of experiments is to show whether we can use an SLA 3D to micropattern a film of photoresist spin-coated onto a Silicon wafer. This step is the starting point of every photolithography process. This approach is analogous to classic flood-expose through a photomask, except in this approach the photomask is digitally created from a CAD file and not a physically manufactured part that makes rapid prototyping impossible and redesigns costly and slow. Direct-write lithography tools like the Heidelberg MLA150 exist for flexible designs but are both very expensive (~100,000s USD) and comparably slow, especially for larger area (up to 6 inch) exposures due to the nature of tracing out the input pattern.  

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/Elegoo_Mars3_printer.png" width="20%" />

Here, we use a 350$ SLA 3D printer, the Elegoo Mars 3, to expose our pattern created in Fusion360 and exported as an STL file. The Elegoo Mars features a 4K 6.6 inch LCD with 4098\*2560 pixels to project an image from a 405nm UV backlight. This yields a pixel-limited resolution of 35 um. While this rival the sub-1-micron resolution of the MLA150, a lithography process using this as an expsosure method may enable micron-scale precision patterning in hobbyist-spaces by being both cheap and space-efficient. Possible fields of applicationa where the here obtained resolution is sufficient are MEMS fabrication, Lab-on-a-chip/Microfluidics, as well as rapid prototyping of tiny and flexible PCBs, but also waveguides, metasurfaces, microanteannas and much more.

## Sample Preparation

The resist used here is [AZ3312](https://cores.research.asu.edu/sites/default/files/2019-10/az_3312_photoresist_data.pdf) is the standard positive photoresist provided by MIT.nano. Sample cleaning was carried out in the Baldo lab by sonicating 1x1 inch samples of cleaved single crystal Silicon in acetone and IPA for 2 minutes each, followed by blow-drying with nitrogen. The resist was spin-coated in the Class 100 cleanroom area within MIT.nano. A Class 100 Cleanroom contains less than 100 particles larger than 0.5 mircons per cubic foot of air. A near-particle-free environment is of utmost importance for a high result yield in micro-fabrication, as dust particles settling on the surface will cause defects in structures created by patterned photoresist on the substrate surface. The AZ3312 was spin-coated at 3000 rpm for 60 seconds onto the Silicon wafers after a 5 min substrate-drying bake step, which improves resist adhesion.  
After resist spinning of soft-bake step was carried out for 90 seconds at 100 C.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3788.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3791.jpeg" width="30%" />

## Calculation of UV exposure time

The required UV exposure dose can be found in the data-sheet linked above to be 100 mJ/cm2. Sensitivity is 0.065 A/W Detected 150 uA yield 2mW. Since the area of the photodiode is 1x1 cm, the UV-light intensity is thus 2 mW/cm2. To obtain the reuqired exposure time from this, one simply needs to divide the exposure dose by the lamp intensity, yielding an exposure time of only *50 seconds*.  

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3785.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3787.JPEG" width="30%" />

## UV-exposure on Elegoo Mars 3 printer

UV exposure was carried out by placing the resist-coated wafer upside down directly on the glass panel of the printer's LCD screen, as shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3794.JPEG" width="30%" />
<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Photos/IMG_3795.JPEG" width="30%" />

## Resist development

The resist was developed in MIT.nano in AZ300 MIF Developer for 90 seconds at room temperature.

## Result Characterization in Optical Microscope 

### 1st experiment: Develop structures in a matrix of undeveloped resist

The CAD structures used in this experiment are depicted below. Since the bodies in the STL file are usually the areas of the resin to be hardened, bodies will be exposed areas on the printer bed. As AZ3312 is a positive resist, exposed areas in the polymer are broken down and will be washed away in the developer. Thus, in the case of the bodies shown below, the pads and lines will wash away while all other resist on the substrate remains in place. From an adhesion perspective, it is evidently a lot easier to develop structures in a matrix of connected resist than vice versa.  
The STL file was imported and sliced in the CHITUBOX software recommended by Elegoo for use in their 3D printer. The height of the bodies to pattern is arbirtary here since we simply set the bottom layer exposure time to the expsoure time calculated above and stop the print after the bottom layer exposure is complete.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/CAD_pads_lines.png" width="30%" />

The structures to be patterned into the resist are pairs of pads ranging from 5 mm down to 10 um side length. The smallest pads are not expected to be possible to develop here since their side length is below the pixel resolution of the printer. Equivalently connected lines are exposed on the right-hand side ranging from 500 um line width to 25 um line width.

Below shown are the results of the first experiment imaged in an optical microscope at 5x magnification.

The image below shows 200 um pads on the very left down to 10 um pads on the very right. A seen in the image pads of 50 um side length and gap cannot be resolved cleanly anymore. Further, note the singular dust particle creating a significant defect in one of the 200 um pads, highlighting the importance of a low-particle environment.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/5x_small_pads_annotated.png" width="30%" />

Notable in the image above is the partly developed border region between exposed and unexposed areas. The width of these poorly defined border regions is very close to 35 microns, matching exactly the pixel size of the display. An explanation for that may be that may be that liquid crystals adjacent in on/off position require 1 pixel in between that let's part of the ligth pass, as indicated in the schematic below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/border_liquid_crystal_alignment.png" width="20%" />

Investigating the developed line patterns, the image below shows the tranisition of the 500 um trace to the 200 um trace. Interestingly, the cleanly developed region inside the trace is close to 250 um wide where it is defined to be 200 um wide in the CAD file. Further the above mentioned partly-exposed border region is clearly visible here and measuring 35 um width as well. 

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/5x_250um_500um_annotated.png" width="30%" />

Due to these poorly exposed border regions the 50 um and 25 um trace widths are not well developed, as shown below.

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Developed_patterns_in_unexposed_resist/Img4-5x_25um_50um_annotated.png" width="30%" />

A solution for this issue of ill-defined border regions could be overexposure of the resist. This should yield a cleaner edge, as the above partly-exposed pixels will develop away with sufficient exposure. This approach will be explored in the second experiment described below.

### 2nd experiment: Develop free-standing resist structures with improved edges by overexposure

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/CAD_pads_lines_inverted.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_200um_line_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_500um_pad_annotated.png" width="30%" />

<img src="/assets/images/Micropatterning_Elegoo_Mars_SLA_3D_printer/220401_1st_pattern_test_AZ3312_on_Si/Resist_around_patterns_developed/5x_200um_pad_annotated.png" width="30%" />

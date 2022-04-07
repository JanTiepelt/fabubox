# Micropatterning of thin films using a SLA 3D Printer 

### in collaboration with Mayuran Saravanapavanantham

Goal of this first set of experiments is to show whether we can use an SLA 3D to micropattern a film of photoresist spin-coated onto a Silicon wafer. This step is the starting point of every photolithography process. This approach is analogous to classic flood-expose through a photomask, except in this approach the photomask is digitally created from a CAD file and not a physically manufactured part that makes rapid prototyping impossible and redesigns costly and slow. Direct-write lithography tools like the Heidelberg MLA150 exist for flexible designs but are both very expensive (~100,000s USD) and comparably slow, especially for larger area (up to 6 inch) exposures due to the nature of tracing out the input pattern.  

Here, we use a 350$ SLA 3D printer, the Elegoo Mars 3, to expose our pattern created in Fusion360 and exported as an STL file. The Elegoo Mars features a 4K 6.6 inch LCD with 4098\*2560 pixels to project an image from a 405nm UV backlight. This yields a pixel-limited resolution of 35 um. While this rival the sub-1-micron resolution of the MLA150, a lithography process using this as an expsosure method may enable micron-scale precision patterning in hobbyist-spaces by being both cheap and space-efficient. Possible fields of applicationa where the here obtained resolution is sufficient are MEMS fabrication, Lab-on-a-chip/Microfluidics, as well as rapid prototyping of tiny and flexible PCBs, but also waveguides, metasurfaces, microanteannas and much more.

## Sample Preparation

The resist used here is [AZ3312](https://cores.research.asu.edu/sites/default/files/2019-10/az_3312_photoresist_data.pdf) is the standard positive photoresist provided by MIT.nano. Sample cleaning was carried out in the Baldo lab by sonicating 1x1 inch samples of cleaved single crystal Silicon in acetone and IPA for 2 minutes each, followed by blow-drying with nitrogen. The resist was spin-coated in the Class 100 cleanroom area within MIT.nano. A Class 100 Cleanroom contains less than 100 particles larger than 0.5 mircons per cubic foot of air. A near-particle-free environment is of utmost importance for a high result yield in micro-fabrication, as dust particles settling on the surface will cause defects in structures created by patterned photoresist on the substrate surface. The AZ3312 was spin-coated at 3000 rpm for 60 seconds onto the Silicon wafers after a 5 min substrate-drying bake step, which improves resist adhesion.  

## Calculation of UV exposure time

The required UV exposure dose can be found in the data-sheet linked above to be 100 mJ/cm2. Sensitivity is 0.065 A/W Detected 150 uA yield 2mW. Since the area of the photodiode is 1x1 cm, the UV-light intensity is thus 2 mW/cm2. To obtain the reuqired exposure time from this, one simply needs to divide the exposure dose by the lamp intensity, yielding an exposure time of only *50 seconds*.  

## UV-exposure on ELegoo Mars 3 printer

## Result Characterization

Below shown is 


---
layout: project
title: MAE 3270 Custom Torque Wrench
description: Advanced Torque Wrench design project with emphasis on materials
technologies: [ANSYS Static Strctural, Autodesk Fusion, MATLAB]


---
<div style="clear: both;"></div>

---

### **1. Images of CAD Model.**


<img src="{{ 'assets\images\Torque Wrench\Isoview Wrench.png' | relative_url }}" alt="Mesh" style="width: 160%; display: block; margin: 0 auto;" />

<img src="{{ 'assets\images\Torque Wrench\Isoview Wrench1.png' | relative_url }}" alt="Mesh" style="width: 160%; display: block; margin: 0 auto;" />

<img src="{{ 'assets\images\Torque Wrench\Isoview Wrench2.png' | relative_url }}" alt="Mesh" style="width: 160%; display: block; margin: 0 auto;" />


---

### **2. Describe material used and its relevant mechanical properties.**

**Material Used:**  
Low Alloy Steel, 300M High Carbon Quenched & Tempered

**Relevant Mechanical Properties:**
- Elastic Modulus:  29*10^6 psi
- Ultimate Tensile Strength: 279 ksi
- Fatigue Strength (10^6 cycles, Stress Ratio = -1):  125 ksi
- Fracture Toughness:  45 ksi.in^0.5 

**Material Justification:**

I am using low alloy steel 300M (high carbon), quenched and tempered for the design of my torque wrench. Furthermore, utilizing this material specifically was important because of the unique material properties. In the base design, I noticed that the fracture factor of safety was the lowest by at least a factor of 3 (in comparison to the other factors of safety), so I realized that either the geometry or material needs to compensate for this shortcoming in the M42 of the base design. I then limited the geometry of the torque wrench to have a square cross section because of usability and consumer interface. Because of this, I needed to find a material with an exceptionally high fracture toughness. The fracture toughness of this material I chose had a fractured toughness of 3x the M42 in the base design.

Beyond just fracture toughness, the fatigue strength is also better than the base design. Although the ultimate tensile strength of 300M is lower than the base design, this choice was acceptable because of the overdesigned choice of M42 for brittle failure. After running the mass reduced and optimized hand calculations, I was able to achieve a fracture facture of safety of 2.0150, fatigue factor of safety of 2.222, and brittle failure factor of safety of 4.9600. This is almost perfectly aligned with the assignment requirements.

Finally, the relatively low Young's Modulus of 29*10^6 psi means inducing a strain large enough to create a 1.0 mV/V power output from a half-bridge Wheatstone Bridge.

---

### **3. Diagram communicating how loads and boundary conditions were applied to your FEM model.**


Description of setup:
- Fixed boundary applied at: top 0.4" of the drive  
- Force (M/L) applied at: end of torque wrench handle  
- Meshing: MultiZone meshing 

Meshing: 
<img src="{{ 'assets/images/Torque Wrench/Mesh.png' | relative_url }}" alt="Mesh" style="width: 160%; display: block; margin: 0 auto;" />


Loading Conditions:
![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\Loading.png" | relative_url }})

---

### **4. Normal strain contours (in the strain gauge direction) from FEM**

Strain direction:  Along X Axis

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\StrainCont.png" | relative_url }})

---

### **5. Contour plot of maximum principal stress from FEM**
![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\StressCont.png" | relative_url }})

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\StressConc.png" | relative_url }})


---

### **6. Summarize results from FEM calculation showing:**
- maximum normal stress: 1.006e5 psi (stress concentration along drive-handle interface fillet)
- load point deflection: 0.91572"
- strains at the strain gauge locations (half bridge): +0.0018103 ε,-0.0018103 ε

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\NormalStress.png" | relative_url }})

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\NormalStressConc.png" | relative_url }})

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\Deform.png" | relative_url }})

![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\StrainProbe.png" | relative_url }})
![Torque Wrench Isoview]({{ "assets\images\Torque Wrench\StrainProbeValue.png" | relative_url }})

---

### **7. Torque wrench sensitivity in mV/V using strains from the FEM analysis**


$$
\frac{V_{\text{out}}}{V_{\text{in}}}
= \frac{k \cdot 2\varepsilon}{4}
$$


$$
k = 2, \qquad \varepsilon = 0.0018103
$$


$$
\frac{V_{\text{out}}}{V_{\text{in}}}
= \frac{2 \cdot 2 \cdot 0.0018103}{4}
= 0.00181103
$$

$$
\frac{V_{\text{out}}}{V_{\text{in}}}
= 1.811 \text{ mV/V} \;>\; 1 \text{ mV/V}
$$



---

### **8. Strain gauge selected (give type and dimensions). Note that design must physically have enough space to bond the gauges.**
The Omega Engineering Linear 1 Axis SGD-7/350-LY11 strain gauge is the best option for my torque wrench. This is because the high resistance of 350 Ohms means that a larger output voltage can be drawn as prove by the infamous formula V = I*R. Additionally, the carrier width is only 0.201" tall leaving 0.4-0.201 = 0.199" of space for bonding the strain gauge to the torque wrench. As per my hand calculation I will be placing the strain gauge 1 inch from the drive, on the side experiencing positive stress (in tension).

**Strain Gauge:**  
 Omega Engineering Linear 1 Axis SGD-7/350-LY11
<img src="{{ 'assets/images/Torque Wrench/Omega.png' | relative_url }}" alt="Mesh" style="width: 160%; display: block; margin: 0 auto;" />

**Dimensions & Specs:**
- Gauge Length:  0.256"
- Gauge Width:  0.122"
- Carrier Dimensions:  0.449" x 0.201"
- Resistance:  350 Ohms



---


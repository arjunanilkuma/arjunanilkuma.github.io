---
layout: post
title: "Gearbox Design"
date: 2026-04-20
categories: engineering projects
---

# ME 354: Two-Stage Gearbox Design Report

## Introduction
The objective of this project is the design of a two-stage spur gear transmission system for an electric go-kart application. The gearbox is required to interface with an electric motor providing 50 hp at 10,000 rpm, reducing the rotational speed to 500 rpm at the drive wheels. Per the Project Statement, a full-floating axle design is utilized to ensure the drive shaft carries only the torsional load, while a horizontal net force of 300 lbf per wheel is considered for the assembly.The design focus is centered on the intermediate shaft, which must support the primary torque transformation while maintaining mechanical integrity under fatigue loading. The design process follows an iterative approach—balancing gear bore constraints with minimum shaft diameter requirements—to achieve a factor of safety $n \geq 1.5$. All components, including gears, bearings, and keys, are sourced from McMaster-Carr and Misumi to ensure commercial availability and standardized manufacturing tolerances.
## 2. Power, Torque, and Gear Ratio Requirements
### 2.1 Torque Calculations
Input torque ($T_{in}$):
$$
\begin{align}
H  & =  \frac{T_{in}\omega_{in}}{5252}  \\
T_{in} &  = 5252 \times \frac{H}{\omega_{in}}  \\
 & = 5252 \times \frac{50\text{ hp}}{10,000\text{ rpm}}  \\
 & = 26.26 \text{ lb-ft}
\end{align}
$$
Output torque ($T_{out}$):
$$
\begin{align}
T_{in}\omega_{in}   & =T_{out}\omega_{out} \\
T_{out}   &  =  \frac{T_{in}\omega_{in}}{\omega_{out}} \\
 &  = \frac{26.26\text{ lb-ft}*10,000\text{ rpm}}{500\text{ rpm}}  \\
 & = 525.2\text{ lb-ft}
\end{align}
$$
### 2.2 Gear Ratios
$$e = \frac{500}{10,000} = \frac{1}{20} = \left(\frac{1}{4}\right)\left(\frac{1}{5}\right)$$
### 2.3 : Gear Specification

The smallest number of the teeth, $N_{1}$, on the pinion for the first set of gears without interference assuming pitch angle $\phi=20\degree$ and full depth teeth ($k=1$):
$$
\begin{align}
N_{P} & =\frac{2k}{(1+2m)\sin^2\phi}(m+\sqrt{m^2+(1+2m)\sin^2\phi }) \\
N_{1}& =\frac{2(1)}{(1+2(4))\sin^2(20\degree)}((4)+\sqrt{(4)^2+(1+2(4))\sin^2(20\degree )}) \\ \\
 & =15.4436 \to 16\text{ teeth}
\end{align}
$$
and for the pinion on the second set of gears:
$$
\begin{align}
N_{1}& =\frac{2(1)}{(1+2(5))\sin^2(20\degree)}((5)+\sqrt{(5)^2+(1+2(5))\sin^2(20\degree )}) \\ \\
 & = 15.7405 \to 16\text{ teeth}
\end{align}
$$
Proceed with:
$$
\begin{align}
N_{1}=16\text{ teeth}, \qquad N_{2}=64\text{ teeth}, \qquad N_{3}=16\text{ teeth},\qquad N_{4}=80\text{ teeth}, 
\end{align}
$$
finding the angular velocity of $\omega_{2}$ (since they share the same intermediate shaft, also, finding $\omega_{3}$):
$$
\begin{align}
\frac{\omega_{2}}{10,000\text{ rpm}}=\frac{N_{1}}{N_{2}}=\frac{1}{4}\to \omega_{2}=2,500\text{ rpm} \\
\omega_{2}=\omega_{3}=2,500 \text{ rpm}
\end{align}
$$
determining torques of the intermediate shaft:
$$
\begin{align}
T_{2}=T_{3}=5,252\times \frac{50\text{ hp}}{2,500\text{ rpm}} = 105.04\text{ lb-ft}
\end{align}
$$

Starting with a Module $M$ 1.5 (subject to change after testing AGMA stresses), then pitch diameter $d_{p}$ of each gear is:
$$
\begin{align}
d_{p} & =M\times N \\
d_{1} &  = 1.5 \times 16 = 24\text{ mm} = 0.9449\text{ in} \\
d_{2} &  = 1.5 \times 64 = 96 \text{ mm} = 3.780\text{ in} \\
d_{3} &  = 1.5 \times 16 = 24\text{ mm} = 0.9449\text{ in} \\
d_{4} &  = 1.5 \times 80 = 120\text{ mm} = 4.724\text{ in}
\end{align}
$$
Next, we will choose a gear 3 to start our analysis (and also gears 1 and 2)

## 3. Intermediate Shaft Iterative Design
### First Iteration:
To begin, find meshing gears to analyze the intermediate shaft:

| Gear # | Module | Number of Teeth | Pitch Diameter (mm(in)) | Pressure Angle (deg) | Face Width (mm(in)) | Total Width (mm) | Bore Diameter (mm) | Bending Strength (Nm(lb-ft)) |
| ------ | ------ | --------------- | ----------------------- | -------------------- | ------------------- | ---------------- | ------------------ | ---------------------------- |
| 3      | 1.5    | 16              | $24 (0.945)$            | 20$\degree$          | $15(0.591)$         | $15(0.591)$      | $8N-12N$           | 8.93 (6.59)                  |
| 2      | 1.5    | 64              | $96 (3.780)$            | 20$\degree$          | $15(0.591)$         | $15(0.591)$      | $12N-37N$          | 56.99 (42.03)                |
| 1      | 1.3    | 16              | $24 (0.945)$            | 20$\degree$          | $15(0.591)$         | $15(0.591)$      | $8N-12N$           | 8.93 (5.59)                  |
And some bearings:

| Bearing part number | Width (mm) | Inner Diameter (mm) | Outer Diameter (mm) | Max RPM |
| ------------------- | ---------- | ------------------- | ------------------- | ------- |
| SB6201ZZ            | 10         | 12                  | 32                  | 22,000  |

In order to solve for reaction forces, we must first find the locations of the gears and bearings on the shaft. Leaving 1-inch on both ends of the shaft as excess and a $\frac{1}{2}$ inch clearance between the bearing and gears to fit tools in (seen below, note locations A, B, C, and D marked in red, as they will be referred to later on), we get shoulder length of 6.204 in.
![[Screenshot 2026-04-12 at 12.35.33 AM.png|666]]


Now, calculating the tangential ($W_{t_{2}}, W_{t_{3}}$) forces on gears 2 and 3 (red arrows seen below in Figure 1.2):![[Screenshot 2026-04-12 at 1.52.07 AM.png|666]]
$$
\begin{align}
W_{t_{2}}  & = \frac{T_{2}}{\frac{d_{2}}{2} \left( \frac{1}{12} \right)} = \frac{105.04}{\frac{3.780}{2} (\frac{1}{12})} = 667.00 \text{ lbf} \\
W_{t_{3}}  & = \frac{T_{3}}{\frac{d_{3}}{2} \left( \frac{1}{12} \right)} = \frac{105.04}{\frac{0.945}{2} (\frac{1}{12})} = 2668.02 \text{ lbf}
\end{align}
$$
where $T$ is torque and $d$ is pitch diameter

Note: Because a full-floating design is utilized, the output shaft is isolated from the 300 lbf vertical vehicle load. The output shaft carries only the torsional load of $525.2 \text{ lb-ft}$.

And the radial ($W_{r_{2}}, W_{r_{3}}$) forces:
$$
\begin{align}
W_{r_{2}} & = W_{t_{2}}\times \tan(\phi) =667.00 \times \tan^{-1}(20\degree) = 242.77\text{ lbf}\\ \\
W_{r_{3}} & = W_{t_{3}}\times \tan(\phi) =2668.02 \times \tan^{-1}(20\degree) = 971.08\text{ lbf}\\
\end{align}
$$
where $W_{t}$ is the tangential force and $\phi$ is the pitch angle of the gear


Using these forces, we can take the moment about point A (see Figure 1.1 for points) to find reaction forces of the bearing at point D in the y-direction:
$$
R_{dy} = \frac{{W_{t_{2}} \times (\text{dist. from center of bearing to Gear 2}) - W_{t_{3}} \times (\text{dist. fromcenter to bearing to Gear 3})}}{\text{(distance from center of bearing to center of other bearing})} 
$$
$$
R_{dy}   = \frac{{(666.93\text{ lbf} \times 1.228\text{ in})+(2667.73\text{ lbf}\times 8.437 \text{ in})}}{9.6063\text{ in}} = -2257.97\text{ lbf}
$$
And repeating for the z-direction:
$$
R_{dz} = \frac{{W_{r_{2}} \times (\text{dist. from center of bearing to Gear 2}) - W_{r_{3}} \times (\text{dist. fromcenter to bearing to Gear 3})}}{\text{(distance from center of bearing to center of other bearing})} 
$$
$$
R_{dz}   =\frac{{(242.77\text{ lbf} \times 1.228\text{ in})+(971.08\text{ lbf}\times 8.437 \text{ in})}}{9.6063\text{ in}} = 883.92\text{ lbf}
$$
Summing the forces in the y- and z-directions, we can solve for the reaction forces of the bearing at point A:
$$
\begin{align}
R_{ay} &  = W_{t_{2}}-W_{t_{3}}-R_{dy} = 667.00 - 2668.02 - ( - 2257.97) = 256.96 \text{ lbf} \\
R_{az}  & = W_{r_{2}} + W_{r_{3}}- R_{dz} = 242.77 +971.08 - 883.92 = 329.93 \text{ lbf}
\end{align}
$$
Then, plotting the shear and Moment Diagrams:
![[Screenshot 2026-04-12 at 6.21.16 PM.png|666]]

Taking the shoulder just left of gear 3 as a critical point ($x_{critical}=9.162$, the moment here becomes:
$$
\begin{align}
M_{y,critical} &  = R_{ay}(x_{critical}-x_{a}) - W_{t_{2}}(x_{critical}-x_{G_{2}}) \\
 & = 256.96(9.162 - 1.1969) - 667.00(9.162-2.366) = 2726.53 \text{ lb-in} \\
M_{z,critical} &  = -R_{az}(x_{critical}-x_{a})-W_{r_{2}}(x_{critical}-x_{G_{2}}) \\
 & =-(-93.526)(9.162 - 1.1969) - 242.770(9.162-2.366)= 890.45\text{ lb-in}
\end{align}
$$
so the combined moment at the shoulder is:
$$
\begin{align}
M_{critical} = \sqrt{ M_{y,critical}^2+M_{z,critical}^2 } = 2868.26 \text{ lb-in}
\end{align}
$$
### First Iteration
Since this is our first iteration, there is no prior shaft diameter to modify, so the modified Goodman criterion was applied. Fatigue stress concentration factors were estimated based on a well-rounded shoulder fillet to ensure a robust design regardless of minor diameter iterations. The factors were found from Shigley's and are the following:
$$
\begin{align}
q = 0.8,  &\qquad (\text{Fig. 6-26}) \\
q_{s} = 0.85,  &\qquad (\text{Fig. 6-27}) \\
K_{t}= 1.6,  &\qquad (\text{Fig. A-15-8}) \\ 
K_{ts}= 1.35,  &\qquad (\text{Fig. A-15-9}) \\
\end{align}
$$
From this we can calculate Fatigue Factors:
$$
\begin{align}
K_{f} & =1+q(K_{t}-1)=1+0.8(1.6-1)= 1.48 \\
K_{fs} & =1+q_{s}(K_{ts}-1)=1+0.85(1.35-1) = 1.298
\end{align}
$$
Since the shaft was experiencing a fully reversed loading, the endurance limit $S_{e}$ was corrected using Marin factors for a cold-drawn AISI 1045 steel shaft (using $S_{ut} = 91 \text{ kpsi}$ from Shigley's). This $S_{ut}$ gives $S_{e}' = 0.5\times S_{ut}=45.5\text{ kpsi}$. Additionally the alternating and midrange moment and torque can be found:
$$
\begin{align}
M_{a} & = M_{critical} = 2868.26 \text{ lb-in} \\
M_{m} & =0; \\
T_{a} & = 0; \\
T_{m} & = T_{\text{int}} \times 12 = 1260.5 \text{lb-in}
\end{align}
$$


Now, calculating the Marin factors:
$$
\begin{align}
k_{a} & = 2.0 \times S_{ut}^{-0.217}= 1.234 \\
\text{(assume shaft diameter = 1 inch)}\qquad k_{b}  & =0.879\times(\approx 1\text{ inch})^{-0.107} = 0.879  \\
\text{(combined loading, value is unity)}\qquad k_{c} & =1 \\
\text{(operating at room temperature)}\qquad k_{d}  & = 1 \\
\text{(assume 99\% reliability)}\qquad k_{e} & = 0.814
\end{align}
$$
and solving for corrected endurance limit:
$$
\begin{align}
S_{e}  & = k_{a}k_{b}k_{c}k_{d}k_{e}\times S_{e}' \\
S_{e} & = (1.234)(0.879)(1)(1)(0.814)\times(45.5) = 40.17 \text{ kpsi}
\end{align}
$$
Using the corrected endurance limit, we can use the ASME Shaft Design Equation to calculate the minimum required diameter of a power-transmission shaft to prevent fatigue failure under combined loading as following:
$$
\begin{align}
d = \left( \frac{16n}{\pi} \left( \frac{A}{S_e} + \frac{B}{S_{ut}} \right) \right)^{1/3}
\end{align}
$$
where 
$$
\begin{align}
A  & = \sqrt{4(K_f M_a)^2 + 3(K_{fs} T_a)^2} \\
B  & = \sqrt{4(K_f M_m)^2 + 3(K_{fs} T_m)^2}
\end{align}
$$
and $n$ is the desired factor of safety.

Plugging in using the values found earlier, we find that the required shaft diameter is $1.4242 \text{ in}$ which is much bigger than our maximum bore size of $12\text{ mm} = 0.4724\text{ inch}$. In fact, we can use the maximum bore diameter to see what theoretical factor of safety a shaft limited by our gear's bore would be...
$$
\begin{align}
n  & = \frac{\pi\times(0.4724)^3}{16}\times\left( \frac{A}{S_{e}(\text{psi})} + \frac{B}{S_{ut}(\text{psi})} \right){-1} \\
 & = 0.0547
\end{align}
$$
This tells us that a significant increase in inner bore diameter is required in order to fit a gear onto the correct sized shaft. Because the required shaft diameter ($1.42 \text{ in}$) exceeds the physical limits of the 1.5-Module gear, it would be wise to use a larger Module (e.g. Module 3.0) to provide a sufficient bore diameter for the intermediate shaft. 


#### Second Iteration

To begin the second iteration, we will pick a new gear 3, with Module 3.0:

| Gear # | Module | Number of Teeth | Pitch Diameter (mm(in)) | Pressure Angle (deg) | Face Width (mm(in)) | Total Width (mm) | Bore Diameter (mm) | Bending Strength (Nm(lb-ft)) |
| ------ | ------ | --------------- | ----------------------- | -------------------- | ------------------- | ---------------- | ------------------ | ---------------------------- |
| 3      | 3.0    | 20              | $60(2.362)$             | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 20N-31N            | 171.01 (126.13)              |
| 2      | 3.0    | 80              | $240(9.449)$            | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 25                 | 763 (562.76)                 |
| 1      | 3.0    | 20              | $60(2.362)$             | 20$\degree$          | $30(1.811)$         | $30(1.1811)$     | 20N-31N            | 171.01 (126.13)              |

And new bearings

| Bearing part number | Width (mm) | Inner Diameter (mm) | Outer Diameter (mm) | Max RPM |
| ------------------- | ---------- | ------------------- | ------------------- | ------- |
| B6905ZZ             | 9          | 25                  | 42                  | 16,000  |

With the increase of the module to 3.0, the pitch diameters changed significantly, reducing the tangential forces and increasing the allowable bending stress. Using Matlab, the new alternating moment and midrange torques were found:
$$
\begin{align}
M_{a}  & = 1216.31\text{ lb-in} \\
T_{m} & =1260.46\text{ lb-in}
\end{align}
$$
From the modified Goodman, the ASME shaft equation yielded a new minimum diameter:
$$
\begin{align}
d_{min} & = 1.120 \text{ in} \\
n_{y}  & = 4.64\qquad \text{ (safe)} \\
N  & = 1.51 \times 10^7 \text{ (meets infinite life criteria)}
\end{align}
$$
While the Module 3.0 gears successfully passed the bending strength requirements, there is still a physical mounting conflict. The minimum diameter is $1.120 \text{ in}$ for a factor of safety $n_{f}=1.5$, however the 2nd gear has a bore diameter of $25 mm = 0.984 \text{ in}$, which is smaller than the shaft. The shaft is still too large to fit through Gear 2, so a third iteration is required to select a Gear 2 with a larger configurable bore or further optimize the shaft geometry to reduce the required diameter at the Gear 2 mounting location.

### Third Iteration
Since the last iteration was quite close to passing, on this iteration, the tangential forces could be alleviated by a small amount by increasing the tooth count of gear 3, possibly dropping the bending moment enough to have a small enough minimum diameter that could fit in the $25\text{ mm}$ bore of Gear 2. Below are the gears used for the third iteration. 

| Gear # | Module | Number of Teeth | Pitch Diameter (mm(in)) | Pressure Angle (deg) | Face Width (mm(in)) | Total Width (mm) | Bore Diameter (mm) | Bending Strength (Nm(lb-ft)) |
| ------ | ------ | --------------- | ----------------------- | -------------------- | ------------------- | ---------------- | ------------------ | ---------------------------- |
| 3      | 3.0    | 25              | $75(2.953)$             | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 30                 | 214 (157.84)                 |
| 2      | 3.0    | 80              | $240(9.449)$            | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 25                 | 763 (562.76)                 |
| 1      | 3.0    | 20              | $60(2.362)$             | 20$\degree$          | $30(1.811)$         | $30(1.1811)$     | 20N-31N            | 171.01 (126.13)              |

In this third iteration, the tooth count for Gear 3 was increased from 20 to 25 teeth (increasing the Pitch diameter to $75 \text{ mm}$). The goal of this change was to increase the torque radius, thereby reducing the tangential forces and consequently the bending moments that would dictate the minimum shaft diameter. From the Matlab:
$$
\begin{align}
M_{critical}  & =  984.02 \text{ lb-in}\\ 
d_{min}  & = 1.050\text{ in} \\
\end{align}
$$

### Fourth Iteration
For the fourth iteration, because the gears are so close to passing, the bearings will be adjusted. The $9 \text{ mm}$ bearings move reactions slightly further away from critical points, so making them smaller should, in theory, lower the critical Moment. Below is the new bearing for the fourth iteration. The gears will remain the same as in the third iteration.

| Bearing part number | Width (mm) | Inner Diameter (mm) | Outer Diameter (mm) | Max RPM |
| ------------------- | ---------- | ------------------- | ------------------- | ------- |
| B6805ZZ             | 7          | 25                  | 37                  | 18000   |

Because the change in size between the previous bearings and this iteration's was so small, the change in minimum shaft diameter and critical moment are minuscule.
$$
\begin{align}
M_{critical}  & = 958.16 \text{ lb-in} \\
d_{min} & = 1.0410 \text{ in}
\end{align}
$$
This change is so small, that the trade-off in load rating could become a problem later on.


### Fifth Iteration
For the fifth iteration, the shaft material will be adjusted. Since bending moments have been the critical problem, and not fatigue stress, increasing the $S_{ut}$ could lead to favorable results. Instead of using AISI 1045 CD, this iteration will be done using AISI 1050 CD, which has higher ultimate and yield strengths (note: the bearings will be changed back to the $9\text{ mm}$ width). 
$$
\begin{align}
S_{ut,1050} & = 100\text{ kpsi} \\
S_{Y, 1050} & = 84\text{ kpsi}
\end{align}
$$
This change in material did decrease the minimum shaft diameter as expected:
$$
\begin{align}
d_{min} & = 1.0214 \text{ in}
\end{align}
$$
however, not enough to fit Gear 2 and maintain a factor of safety $n_{f}\geq 1.5$. 

### Sixth Iteration
For the sixth iteration, the number of teeth on Gear 3 will be increased again, similar to the third iteration. The gears used in the table below will be used as well as changes made in prior iterations.

| Gear # | Module | Number of Teeth | Pitch Diameter (mm(in)) | Pressure Angle (deg) | Face Width (mm(in)) | Total Width (mm) | Bore Diameter (mm) | Bending Strength (Nm(lb-ft)) |
| ------ | ------ | --------------- | ----------------------- | -------------------- | ------------------- | ---------------- | ------------------ | ---------------------------- |
| 3      | 3.0    | 30              | $90(3.543)$             | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 25N-49N            | 302.72 (223.27)              |
| 2      | 3.0    | 80              | $240(9.449)$            | 20$\degree$          | $30(1.1811)$        | $30(1.1811)$     | 25                 | 763 (562.76)                 |
| 1      | 3.0    | 20              | $60(2.362)$             | 20$\degree$          | $30(1.811)$         | $30(1.1811)$     | 20N-35N            | 171.01 (126.13)              |
This sixth iteration turned out to be enough to give us an intermediate shaft that fits into both the gears. Both the critical moment and minimum shaft diameter decreased, and the factor of safety $n_{f}>1.5$:
$$
\begin{align}
M_{critical}  & = 829.23 \text{ lb-in} \\
d_{min} & = 0.9761 \text{ in} \\
n_{f} & =1.5383
\end{align}
$$
The final stage of the design process is verifying the mechanical integrity of the selected gears. Above, the structural limits of the intermediate shaft were discussed, but here, the American Gear Manufacturers Association (AGMA) standards will be used to evaluate the gears against both bending and surface wear (pitting).

### AGMA Stresses

To ensure the gearbox will be able to transmit $50\text{ hp}$ at high rotational speeds, the AGMA bending $\sigma_{b}$ and contact $\sigma_{c}$ stress will be calculated. These will then be compared to the allowable material strengths ($S_{ut}, S_{y}$) and adjusted by a series of factors. Below is the AGMA bending stress equation:
$$
\begin{align}
\sigma_{b}= W^tK_{o}K_{v}K_{s} \frac{P}{F} \frac{K_{m}K_{B}}{J}
\end{align}
$$
- $W^t$ is the tangential transmitted load (lbf)
- $K_{o}$ is the overload factor
- $K_{v}$ is the dynamic factor
- $K_{s}$ is the size factor
- $P$ is the transverse diametral pitch
- $F$ is the face width of the narrower gear
- $K_{m}$ is the load-distribution factor
- $K_{B}$ is the rim-thickness factor
- $J$ is the geometry factor

And the AGMA pitting equation:
$$
\begin{align}
\sigma_{c} = C_{p}\left( W^tK_{o}K_{v}K_{s} \frac{K_{m}}{d_{p}F} \frac{C_{f}}{I} \right)^{1/2}
\end{align}
$$
- $C_{p}$ is the elastic coefficient ($\sqrt{ \frac{\text{lbf}}{\text{in}^2} }$)
- $C_{f}$ is the surface condition factor
- $d_{p}$ is the pitch diameter of the pinion
- $I$ is the geometry factor for the pitting resistance

Starting with the bending stress, a $Q_{v}$ is chosen based on the pitch-line velocity. For high-speed applications like this, $Q_{v}= 10$ will be used
$$
\begin{align}
B  & = 0.25(12 - Q_v)^{2/3} \\
A  & =  50 + 56(1 - B)\\
K_v  & = \left( \frac{A + \sqrt{V}}{A} \right)^B \\
K_{v} & = 1.1975
\end{align}
$$
Material Properties for induction-hardened S45C steel give $S_{ut}=55,000 \text{ psi}$ and for gear 3, gives:
$$
\begin{align}
\sigma_{b}  & = 24,121.94 \text{ psi} \\
\sigma_{all} & = 43,054.14 \text{ psi}  \\
n_{b} & = 1.78
\end{align}
$$
This factor of safety exceeds the requirement of 1.5, confirming the tooth root strength is sufficient for the application life of $10^{-7}$ cycles.

For contact stress and pitting resistance, surface durability was evaluated to ensure the gear faces do not experience premature pitting or wear. An elastic coefficient ($C_p$) of **$2300$** was used for the steel-on-steel mesh. With a contact strength ($S_c$) of **$190,000 \text{ psi}$**, the surface analysis results are:
$$
\begin{align}
\sigma_{c} & =112,717.19 \text{ psi} \\
\sigma_{c,all}  & =172,724.52 \text{ psi} \\
n_{c} & =1.53
\end{align}
$$
This also exceeds 1.5, so gear 3 is not going to experience premature pitting or wear. An elastic coefficient $C_{p}$ of 2300 was used for the steel-on-steel mesh with a contact strength of $S_{c}=190,000 \text{ psi}$. Below is a list of intermediate factors used:
$$
\begin{align}
K_{v} &  = 1.1975 \\
K_{s} & =1.1389  \\
K_{m} & =1.1098 \\
K_{B} & =1.000 \\
I & =0.1339 \\
J  & = 0.4000 &  \\

\end{align}
$$

### Keyways
To transmit the torque of $105.04 \text{ lb-ft}$ from the intermediate shaft to the gears, standard parallel keys were selected. A high-strength carbon steel key stock was chosen. The material properties were updated to match AISI 1045 CD ($S_{y} \approx 101.5 \text{ kpsi}$) to ensure the key does not become the weak point in the assembly. The specifications are as follow:
- **Material:** AISI 1050 Steel ($S_{y} = 101,526 \text{ psi}$)
- **Width ($w$):** $8 \text{ mm}$ ($0.3150 \text{ in}$)
- **Height ($h$):** $7 \text{ mm}$ ($0.2756 \text{ in}$)
- **Length ($L$):** $30 \text{ mm}$ ($1.1811 \text{ in}$)
- **Shaft Diameter ($d$):** $25 \text{ mm}$ ($0.9843 \text{ in}$)
- **Shaft Radius ($r$):** $12.5 \text{ mm}$ ($0.4921 \text{ in}$)

The key was evaluated for failure under two primary modes: direct shear and bearing (crushing) stress. The tangential force $F_{t}$ acting at the shaft surface is:
$$\begin{align} F_{t} = \frac{T}{r} = \frac{1260.48 \text{ lb-in}}{0.4921 \text{ in}} = 2561.43 \text{ lbf} \end{align}$$

Using the Distortion Energy Theory for shear yield strength ($S_{sy} = 0.577 S_{y}$):
$$\begin{align} \tau & = \frac{F_{t}}{w \times L} = \frac{2561.43}{0.3150 \times 1.1811} = 6885.56 \text{ psi} \\ n_{shear} & = \frac{0.577 \times S_{y}}{\tau} = \frac{0.577 \times 101,526}{6885.56} = 8.51 \end{align}$$

The bearing stress is calculated based on the area of the key face in contact with the shaft/gear ($h/2 \times L$):
$$\begin{align} \sigma_{c} & = \frac{F_{t}}{\frac{h}{2} \times L} = \frac{2561.43}{0.1378 \times 1.1811} = 15,737.71 \text{ psi} \\ n_{crush} & = \frac{S_{yc}}{\sigma_{c}} = \frac{101,526}{15,737.71} = 6.45 \end{align}$$

The selected key length of $30 \text{ mm}$ provides a robust design with factors of safety significantly exceeding the $n \geq 1.5$ requirement. This length also matches the face width of the gears, ensuring full torque distribution across the gear hub.

### Final Iteration:
After six iterations to resolve the gear bore vs. shaft diameter conflict, the following parameters were finalized:

| Bearing Parameters              | Value   |
| ------------------------------- | ------- |
| Catalog Number (Misumi)         | B6905ZZ |
| Load rating, $C_{0}$            | 3.19    |
| Inner Diameter (mm), $d$        | 25 mm   |
| Outer Diameter (mm), $D$        | 42      |
| Width (mm), $B$                 | 9       |
| Allowable Rotation Speeds (rpm) | 16,000  |

| Gear 1 Parameters                | Value                 |
| -------------------------------- | --------------------- |
| Part # (Misumi)                  | GEAKBH3.0-20-30-A-25N |
| Number of Teeth                  | 20                    |
| Module                           | 3.0                   |
| Bore Diameter, $d$               | 25 mm                 |
| Outer Diameter, $D$              | 60 mm                 |
| Face , $B$                       | 30 mm                 |
| Allowable Bending Strength (lbf) | 126.12                |


| Gear 2 Parameters                | Value      |
| -------------------------------- | ---------- |
| Part # (Misumi)                  | SSA3-80J25 |
| Number of Teeth                  | 80         |
| Module (mm)                      | 3.0        |
| Bore Diameter (mm), $d$          | 25 mm      |
| Pitch Diameter (mm), $D$         | 240 mm     |
| Face (mm), $B$                   | 30 mm      |
| Allowable Bending Strength (lbf) | 155        |


| Gear 3 Parameters                | Value                 |
| -------------------------------- | --------------------- |
| Part # (Misumi)                  | GEAKBH3.0-30-30-A-25N |
| Number of Teeth                  | 30                    |
| Module (mm)                      | 3.0                   |
| Bore Diameter (mm), $d$          | 25 mm                 |
| Pitch Diameter (mm), $D$         | 90 mm                 |
| Face (mm), $B$                   | 30 mm                 |
| Allowable Bending Strength (lbf) | 223.27                |

| Retaining Rings Parameters | Value     |
| -------------------------- | --------- |
| Part # (McMaster           | 99142A410 |
| Diameter                   | 21.9 mm   |

| Shaft Parameters               | Value        |
| :----------------------------- | :----------- |
| **Material**                   | AISI 1050 CD |
| **Final Diameter ($d_{min}$)** | 25 mm        |
| **Factor of Safety ($n_f$)**   | **1.5383**   |

<div style="page-break-after: always;"></div>

## 4. Component Specifications & Drawings
### 4.1 Final Assembly Drawing

![[Screenshot 2026-04-13 at 11.03.22 PM.png|666]]

### 4.2 2D Dimensioned Drawing
![[Screenshot 2026-04-13 at 11.03.59 PM.png]]
### 4.2: Isometric View of Intermediate Shaft with Gears 2 and 3:
![[Screenshot 2026-04-13 at 9.22.27 PM.png]]


---

## 5. Conclusion
The iterative design process resulted in a robust two-stage gearbox that successfully meets all specified power and speed requirements. The final configuration utilizes a Module 3.0 gear set and an AISI 1050 CD intermediate shaft with a diameter of 25 mm. This assembly achieved a minimum fatigue factor of safety of 1.54 and an AGMA bending factor of safety of 1.78, ensuring infinite life for the shaft and high durability for the gear teeth.


## Appendix: Computational Calculations & Technical Justifications

### A.1 Stress Concentration & Notch Sensitivity Justification

From Table 7-1 in Shigley's the following ratios were used to determine the stress concentration factors at the critical shoulder (Iteration 6, $d = 25\text{ mm}$):
- Geometry Ratios: Assuming a shoulder diameter $D = 30\text{ mm}$ and a fillet radius $r = 1.25\text{ mm}$:
    - $D/d = 1.20$
    - $r/d = 0.05$
- Theoretical Factors: $K_{t} = 1.60$ (Bending)
    - $K_{ts} = 1.35$ (Torsion)
- Notch Sensitivity ($q$): For AISI 1050 CD ($S_{ut} = 100\text{ kpsi}$) and $r = 0.05\text{ in}$:
    - $q \approx 0.80$ (Fig. 6-26)
    - $q_{s} \approx 0.85$ (Fig. 6-27)
### A.2 AGMA Factor Selection & Geometry
The following factors were utilized for the Part 4 mechanical integrity verification of Gear 3:
- Geometry Factor ($J$): Value of 0.40 was found from Fig. 14-6 for a 30-tooth pinion meshing with an 80-tooth gear    
- Geometry Factor ($I$): Calculated as 0.1339 for a $20^\circ$ pressure angle and stage ratio $m_G = 2.67$.
- Load Distribution ($K_m$): Assumed "Commercial Enclosed Unit" with $F = 1.18\text{ in}$.
- Dynamic Factor ($K_v$): Calculated using $Q_v = 10$ for high-speed motor application.
### A.3 Intermediate Shaft Bearing Life Analysis
To verify the suitability of the Misumi B6905ZZ bearings, the $L_{10}$ life was estimated using the reaction forces from Part 3 ($R_{ay}, R_{az}, R_{dy}, R_{dz}$):
$$\begin{align} R_{A,total} & = \sqrt{256.96^2 + 329.93^2} = 418.18\text{ lbf} \\ R_{D,total} & = \sqrt{(-2257.97)^2 + 883.92^2} = 2424.81\text{ lbf} \end{align}$$

Using the load rating $C_0 = 3.19\text{ kN}$ ($717\text{ lbf}$) and a shaft speed of 2,500 rpm, the bearing at point D is the limiting component. Given the high-speed and load requirements, high-precision shielded bearings were selected to ensure the target service life of the go-kart assembly.
#### A.4 Matlab Script
The following script was used to perform the iterative analysis for the intermediate shaft, including the ASME diameter calculations and AGMA stress verification.

```matlab
clear;

Tint = 105.04; % lb-ft

T2 = Tint;

T3 = Tint;

dp_2 = input('Enter pitch diameter of Gear 2 (mm): ') / 25.4;

dp_3 = input('Enter pitch diameter of Gear 3 (mm): ') / 25.4;

fprintf('\n');

B_bearing = input('Enter the width of the bearings on the intermediate shaft (mm): ') / 25.4;

B_gear2 = input('Enter the width of Gear 2 (mm): ') / 25.4;

B_gear3 = input('Enter the width of Gear 3 (mm): ') / 25.4;

% Defining gaps

excess = 1; % both ends have 1in leftove

gap = 0.5; % bearing and gear have 0.5in clearance

fprintf('Assumptions: \nClearance on ends of shaft are 1-in \nGaps between bearings and gears are 0.5-in\n');

bear_to_gear2 = B_bearing/2 + gap + B_gear2/2;

% dist1 = input('Enter distance from the center of Bearing A to the center of Gear 2 (in): ');

gear2_to_gear3 = 12 - (2 * excess) - (2 * gap) - (2 * B_bearing) - B_gear2/2 - B_gear3/2;

% dist2 = input('Enter distance from the center of Gear 2 to the center Gear 3 (in): ');

gear3_to_bear = B_gear3/2 + gap + B_bearing/2;

% dist3 = input('Enter distance from Gear 3 to Bearing D (in): ');

rad_2 = dp_2 / 2;

rad_3 = dp_3 / 2;

% Convert radius from inches to foot (lb-ft)

Wt2 = T2 / (rad_2 / 12);

Wr2 = Wt2 * tand(20);

Wt3 = T3 / (rad_3 / 12);

Wr3 = Wt3 * tand(20);

% Solve unknowns (lbf)

Rdy = (Wt2*bear_to_gear2 + Wt3*(bear_to_gear2+gear2_to_gear3)) / (bear_to_gear2+gear2_to_gear3+gear3_to_bear);

Rdz = (- Wr2*bear_to_gear2 + Wr3*(bear_to_gear2+gear2_to_gear3)) / (bear_to_gear2+gear2_to_gear3+gear3_to_bear);

Ray = Wt2 + Wt3 - Rdy;

Raz = - Wr2 + Wr3 - Rdz;

fprintf('\n--- Forces (lbf) ---\n');

fprintf('Ray = %.4f lbf\n', Ray);

fprintf('Raz = %.4f lbf\n', Raz);

fprintf('Rdy = %.4f lbf\n', Rdy);

fprintf('Rdz = %.4f lbf\n', Rdz);

fprintf('Wt2 = %.4f lbf\n', Wt2);

fprintf('Wt3 = %.4f lbf\n', Wt3);

fprintf('Wr2 = %.4f lbf\n', Wr2);

fprintf('Wr3 = %.4f lbf\n', Wr3);

% set bearing and gear positions

xA = excess + B_bearing/2;

xB = excess + B_bearing/2 + bear_to_gear2;

xC = excess + B_bearing/2 + bear_to_gear2 + gear2_to_gear3;

xD = excess + B_bearing/2 + bear_to_gear2 + gear2_to_gear3 + gear3_to_bear;

x_crit = excess + B_bearing/2 + bear_to_gear2 + gear2_to_gear3 - B_gear3 / 2;

x = linspace(0, 12, 100000);

% --- XY Plane Shear (Vy) in lbf ---

Vy = zeros(size(x));

for i = 1:length(x)

xi = x(i);

if xi >= xA

Vy(i) = Vy(i) + Ray;

end

if xi >= xB

Vy(i) = Vy(i) - Wt2;

end

if xi >= xC

Vy(i) = Vy(i) - Wt3;

end

if xi >= xD

Vy(i) = Vy(i) + Rdy;

end

end

% --- XZ Plane Shear (Vz) in lbf ---

Vz = zeros(size(x));

for i = 1:length(x)

xi = x(i);

if xi >= xA

Vz(i) = Vz(i) + Raz;

end

if xi >= xB

Vz(i) = Vz(i) + Wr2;

end

if xi >= xC

Vz(i) = Vz(i) - Wr3;

end

if xi >= xD

Vz(i) = Vz(i) + Rdz;

end

end

My = cumtrapz(x, Vy);

Mz = cumtrapz(x, Vz);

% Plotting

figure;

subplot(2,2,1);

plot(x, Vy, 'b', 'LineWidth', 1.5);

hold on;

yline(0, 'k--');

xline(xA, 'k:', 'A');

xline(xB, 'k:', 'B');

xline(xC, 'k:', 'C');

xline(xD, 'k:', 'D');

xline(x_crit, 'k:', 'critical shoulder');

title('Shear Diagram - XY Plane');

xlabel('x (in)'); ylabel('V_y (lbf)');

xlim([0 12]);

grid on;

subplot(2,2,3);

plot(x, My, 'r', 'LineWidth', 1.5);

hold on;

yline(0, 'k--');

xline(xA, 'k:', 'A');

xline(xB, 'k:', 'B');

xline(xC, 'k:', 'C');

xline(xD, 'k:', 'D');

xline(x_crit, 'k:', 'critical shoulder');

title('Moment Diagram - XY Plane');

xlabel('x (in)'); ylabel('M_y (in·lbf)');

xlim([0 12]);

grid on;

subplot(2,2,2);

plot(x, Vz, 'b', 'LineWidth', 1.5);

hold on;

yline(0, 'k--');

xline(xA, 'k:', 'A');

xline(xB, 'k:', 'B');

xline(xC, 'k:', 'C');

xline(xD, 'k:', 'D');

xline(x_crit, 'k:', 'critical shoulder');

title('Shear Diagram - XZ Plane');

xlabel('x (in)'); ylabel('V_z (lbf)');

xlim([0 12]);

grid on;

subplot(2,2,4);

plot(x, Mz, 'r', 'LineWidth', 1.5);

hold on;

yline(0, 'k--');

xline(xA, 'k:', 'A');

xline(xB, 'k:', 'B');

xline(xC, 'k:', 'C');

xline(xD, 'k:', 'D');

xline(x_crit, 'k:', 'critical shoulder');

title('Moment Diagram - XZ Plane');

xlabel('x (in)'); ylabel('M_z (in·lbf)');

xlim([0 12]);

grid on;

sgtitle('Shear and Moment Diagrams');

[~, iB] = min(abs(x - xB));

[~, iC] = min(abs(x - xC));

inlbf_to_Nm = 0.112985; % 1 in·lbf = 0.112985 N·m

fprintf('\n--- Key Moment Values ---\n');

fprintf('My at B (x = %.4f in) = %.4f in·lbf', xB, My(iB));

fprintf('My at C (x = %.4f in) = %.4f in·lbf', xC, My(iC));

fprintf('Mz at B (x = %.4f in) = %.4f in·lbf', xB, Mz(iB));

fprintf('Mz at C (x = %.4f in) = %.4f in·lbf', xC, Mz(iC));

% GOODMAN CRITERION

% x_crit = input(['Enter your critical location, based on graphs and assumed shaft geometry (esp shoulder w ' ...

% 'fillet (in) ->']);

% Calculate critical moment values at the specified critical location

[~, iCrit] = min(abs(x - x_crit));

fprintf('My at critical location (x = %.4f in) = %.4f in·lbf | %.4f N·m\n', x_crit, My(iCrit), My(iCrit) * inlbf_to_Nm);

fprintf('Mz at critical location (x = %.4f in) = %.4f in·lbf | %.4f N·m\n', x_crit, Mz(iCrit), Mz(iCrit) * inlbf_to_Nm);

% combined loading

M_comb = sqrt(((My(iCrit))^2) + ((Mz(iCrit))^2));

fprintf('M combined loading at (x = %.4f in) = %.4f in·lbf | %.4f N·m\n', x_crit, M_comb, M_comb * inlbf_to_Nm);

% does user have a previously found diameter?

prev_d_check = input('Do you have a previous shaft diameter to compare against? (y/n) -> ', 's');

if strcmp(prev_d_check, 'y')

prev_d = input('Enter previous shaft diameter (inches) -> ');

end

%Goodman diameter calculations

% --- STRESS CONCENTRATION & NOTCH SENSITIVITY ---

q_input = input('Enter notch sensitivity q (or type "NA" for sharp shoulder assumption): ', 's');

if strcmpi(q_input, 'NA')

% quick assumption for sharp fillets

Kf = 2.7;

Kfs = 2.2;

fprintf('Sharp shoulder assumed: Kf = %.1f, Kfs = %.1f\n', Kf, Kfs);

else

% convert q to double and get specific factors

q = str2double(q_input);

qs = input('Enter shear notch sensitivity qs (often same as q): ');

% ask for Kt and Kts

Kt = input('Enter theoretical stress concentration Kt (bending): ');

Kts = input('Enter theoretical stress concentration Kts (torsion): ');

% calculate fatigue stress concentration factors

Kf = 1 + q * (Kt - 1);

Kfs = 1 + qs * (Kts - 1);

fprintf('Calculated factors: Kf = %.4f, Kfs = %.4f\n', Kf, Kfs);

end

Ma = M_comb;

Mm = 0;

Ta = 0;

Tm = Tint * 12;

A = sqrt((4*(Kf*Ma)^2)+(3*(Kfs*Ta)^2));

B = sqrt((4*(Kf*Mm)^2)+(3*(Kfs*Tm)^2));

n_f = input('Enter your ideal factor of safety (aim for 1.2-1.5, ideally 1.5) -> ');

Sut = input('Enter the ultimate tensile strength in kpsi of your chosen shaft material, cold-drawn -> ');

if Sut <= 200

Se_prime = 0.5 * Sut;

else

Se_prime = 100; % kpsi

end

ka = 2 * (Sut^(-0.217));

% if you do have a previous d calculate kb

if strcmp(prev_d_check, 'y')

kb = 0.879 * prev_d^(-0.107);

else

% if not have them enter. will usually assume 1

kb = input('Enter your kb -> ');

end

kc = 1;

kd = 1; % assume conditions are room temp

ke = 0.814; % asssume 99% reliability

Se = ka * kb * kc * kd * ke * Se_prime;

Se_psi = Se * 1000; % kpsi -> psi

Sut_psi = Sut * 1000; % kpsi -> psi

d_shaft = (16*n_f/pi * (A/Se_psi + B/Sut_psi))^(1/3);

fprintf('d (in) = %.4f\n', d_shaft);

%static loading check based on found d

sig_max = sqrt(((32*Kf*(Mm + Ma)) / (pi*d_shaft^3))^2 + 3*((16*Kfs*(Tm + Ta)) / (pi*d_shaft^3))^2);

Sy = input('Enter yield strength Sy (kpsi) -> ') * 1000;

ny = Sy / sig_max;

fprintf('--- Static Yield Check ---\n');

fprintf('ny = %.4f\n', ny);

if ny > 1

fprintf('Specimen not expected to yield (ny = %.4f)\n', ny);

else

fprintf('WARNING: Yielding expected (ny = %.4f)\n', ny);

end

% von mises

sigma_a = (M_comb * (d_shaft/2))/((pi/64)*d_shaft^4); %psi

sigma_m = 0;

tau_m = (Tm * (d_shaft/2))/((pi/32)*d_shaft^4); %psi

tau_a = 0;

sigma_a_prime = Kf * sigma_a;

sigma_m_prime = sqrt(3 * (Kfs * tau_m)^2);

sigma_ar = sigma_a_prime / (1 - (sigma_m_prime / Sut_psi));

sigma_ar_kpsi = sigma_ar/1000;

f_coeff = input('Enter f (Fig 6-23): ');

a_coeff = ((f_coeff * Sut_psi)^2)/Se_psi;

a_coeff_kpsi = a_coeff/1000;

b_coeff = -(1/3) * log10(((f_coeff * Sut)/Se));

N_cycles_to_failure = (sigma_ar_kpsi/a_coeff_kpsi)^(1/b_coeff);

fprintf('N cycles to failures = %.4f\n', N_cycles_to_failure);

%check fos

d_check = input('Enter a shaft diameter to check: ');

n_check = (pi * d_check^3 / 16) * (A/Se_psi + B/Sut_psi)^-1;

disp(n_check);

% --- AGMA ANALYSIS ---

run_agma = input('\nDo you want to run AGMA analysis? (y/n): ', 's');

if strcmpi(run_agma, 'y')

fprintf('\n--- AGMA ANALYSIS ---\n');

% Select which gear to analyze based on your main script variables

gear_choice = input('Analyze Gear 2 or Gear 3? Enter 2 or 3: ');

if gear_choice == 2

Wt_lbf = Wt2;

pitch_diameter_in = dp_2;

face_width_in = B_gear2;

fprintf('Using Gear 2 values from previous calculations.\n');

elseif gear_choice == 3

Wt_lbf = Wt3;

pitch_diameter_in = dp_3;

face_width_in = B_gear3;

fprintf('Using Gear 3 values from previous calculations.\n');

else

error('Invalid gear selection. Enter 2 or 3.');

end

% Gear-specific inputs

input_speed = input('Enter the original input speed (rpm): ');

stage_1_ratio = input('Enter stage 1 gear ratio: ');

shaft_speed_rpm = input_speed / stage_1_ratio;

module_mm = input('Enter module (mm): ');

diametral_pitch = 25.4 / module_mm; % conversion to teeth/in

Qv = input('Enter AGMA quality number Qv: ');

J = input('Enter AGMA bending geometry factor J: ');

St_psi = input('Enter bending strength number St (psi): ');

Sf = input('Enter design factor for bending Sf: ');

Sc_psi = input('Enter contact strength number Sc (psi): ');

Sh = input('Enter design factor for contact Sh: ');

num_cycles = input('Enter number of load cycles: ');

is_pinion = input('Are you analyzing the pinion? (y/n): ', 's');

% Assumed constants

pressure_angle_rad = deg2rad(20);

Ko = 1.25;

Kt_agma = 1.0;

Kr_agma = 1.0;

Cf = 1.0;

Cp = 2300;

mN = 1.0;

% Dynamic factor Kv

pitch_line_vel = (pi * pitch_diameter_in * shaft_speed_rpm) / 12;

B_kv = 0.25 * (12 - Qv)^(2/3);

A_kv = 50 + 56 * (1 - B_kv);

Kv = ((A_kv + sqrt(pitch_line_vel)) / A_kv)^B_kv;

% Size factor Ks (using your calculated d_shaft)

if d_shaft >= 0.3 && d_shaft <= 2

kb_ks = 0.879 * d_shaft^(-0.107);

elseif d_shaft > 2 && d_shaft <= 10

kb_ks = 0.91 * d_shaft^(-0.157);

else

kb_ks = 1.0; % Default for small diameters

end

Ks = 1 / kb_ks;

% Load distribution factor Km

is_crowned = input('Are the teeth crowned? (y/n): ', 's');

Cmc = 1.0; if strcmpi(is_crowned, 'y'); Cmc = 0.8; end

% Proportion factor Cpf

ratio_term = max(face_width_in / (10 * pitch_diameter_in), 0.05);

if face_width_in <= 1

Cpf = ratio_term - 0.025;

elseif face_width_in <= 17

Cpf = ratio_term - 0.0375 + 0.0125 * face_width_in;

else

Cpf = ratio_term - 0.1109 + 0.0207 * face_width_in - 0.000228 * face_width_in^2;

end

% Mesh alignment factor Cma (Commercial enclosed units)

Cma = 0.0675 + 0.0128 * face_width_in - 0.0000926 * face_width_in^2;

% Location factor Cpm

% Using your xD (total length of active shaft) and position relative to bearings

if gear_choice == 2

dist_to_bear = bear_to_gear2;

else

dist_to_bear = gear3_to_bear;

end

bearing_span = xD - xA;

if (dist_to_bear / bearing_span) < 0.175

Cpm = 1.0;

else

Cpm = 1.1;

end

Km = 1 + Cmc * (Cpf * Cpm + Cma);

% Rim thickness factor KB

tip_d = input('Enter tip diameter (mm): ') / 25.4;

root_d = input('Enter root diameter (mm): ') / 25.4;

bore_d = input('Enter bore diameter (mm): ') / 25.4;

rim_ratio = ((root_d - bore_d) / 2) / ((tip_d - root_d) / 2);

KB = 1.0;

if rim_ratio < 1.2

KB = 1.6 * log(2.242 / rim_ratio);

end

% Bending Stress and Safety Factor

sigma_b = Wt_lbf * Ko * Kv * Ks * (diametral_pitch / face_width_in) * ((Km * KB) / J);

if num_cycles > 3e6

Yn = 1.3558 * num_cycles^(-0.0178);

else

Yn = 6.1514 * num_cycles^(-0.1192);

end

sigma_b_allow = (St_psi / Sf) * (Yn / (Kt_agma * Kr_agma));

n_bending = sigma_b_allow / sigma_b;

% Contact Stress and Safety Factor

mG = input('Enter gear ratio mG (N_gear / N_pinion): ');

I = (cos(pressure_angle_rad) * sin(pressure_angle_rad) / (2 * mN)) * (mG / (mG + 1));

sigma_c = Cp * sqrt(Wt_lbf * Ko * Kv * Ks * (Km / (pitch_diameter_in * face_width_in)) * (Cf / I));

if num_cycles > 1e7

Zn = 1.4488 * num_cycles^(-0.023);

else

Zn = 2.466 * num_cycles^(-0.056);

end

Ch = 1.0;

if ~strcmpi(is_pinion, 'y')

Hbp = input('Enter Brinell hardness of pinion: ');

Hbg = input('Enter Brinell hardness of gear: ');

h_ratio = Hbp / Hbg;

if h_ratio < 1.2; A_p = 0; elseif h_ratio > 1.7; A_p = 0.00698; else; A_p = 0.00898 * h_ratio - 0.00829; end

Ch = 1 + A_p * (mG - 1);

end

sigma_c_allow = (Sc_psi * Zn * Ch) / (Sh * Kt_agma * Kr_agma);

n_contact = sigma_c_allow / sigma_c;

% --- FINAL AGMA OUTPUTS ---

fprintf('\n--- AGMA FINAL RESULTS ---\n');

fprintf('Bending Stress: %.2f psi | Allowable: %.2f psi\n', sigma_b, sigma_b_allow);

fprintf('Bending Safety Factor (n_f): %.4f\n', n_bending);

fprintf('Contact Stress: %.2f psi | Allowable: %.2f psi\n', sigma_c, sigma_c_allow);

fprintf('Contact Safety Factor (n_h): %.4f\n', n_contact);

end
```
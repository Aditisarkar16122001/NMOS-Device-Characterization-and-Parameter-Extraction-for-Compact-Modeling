
# NMOS Device Characterisation and Parameter Extraction: 

##  Project Overview
This project focuses on NMOS transistor characterization and compact modeling using LTspice. Key device parameters were extracted from simulated I–V characteristics and compared with theoretical expectations.



---

##  Objectives

- Simulate NMOS I_d–V_ds Characteristics
- Simulate NMOS I_d-V_GS Characteristics
- Extract compact model parameters
- Compare theoretical vs simulated results
- Analyze short-channel effects
- Evaluate analog performance metrics

---

##  Device Details

| Parameter | Value |
|----------|--------|
| Device | NMOS Level 3 |
| W/L | 10 µm / 1 µm |
| VDS range | 0 – 5 V |
| VGS range | 0 – 5 V |

---

## Schematic in LTSpice: 
![Schematic(2)](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/Schematic%20(2).png)
*Figure 1: NMOS Schematic*
------------------
##  Extracted Parameters

| Parameter | Value | Notes |
|----------|-------|------|
| Threshold Voltage (Vth) | ~1.86 V | From √Id vs Vgs (VDS=5V) |
| gm | 7.09e-4 S | From Id vs VGS slope at VGS = 3V |
| gds | 1.017e-05 S | From Id–Vds slope |
| λ (Channel length modulation) | ~0.022 V⁻¹ | From saturation region |
| ro | ~98.7 kΩ | ro = 1/gds |
| Intrinsic Gain (gm·ro) | ~70 | Analog performance metric |
| Subthreshold slope | ~122 mV/dec | Non-ideal behavior |
| DIBL | ~30 mV/V | Short-channel effect |

---

#  Key Graphs

## ID vs VDS
![Id-Vds](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/Id-Vds.png)
*Figure 2: ID vs VDS Characteristics*
- Here plotting of ID vs VDS is done for VGS = 1V , 2V , 3V , 4V , 5V.
- As Threshold Voltage is 2V as specified in model, we get cutoff region for $V_{GS}<V_{th}$ , and the device gets on for $V_{GS} > V_{th}$. Then for $V_{DS}>(V_{GS}-V_{TH})$ we have the saturation region. 
----
## ID vs VGS ( For VDS = 5V )
![Id-Vgs(Vds=5V)](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/Id-Vgs(Vds%3D5V).png)
*Figure 3: ID vs VGS Characteristics for VGS=5V*
---
## √ID vs VGS (Threshold Extraction)
- For $V_{ds} = 5V$
![sqrtID vs VGS](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/TC(Vds%3D5V).png)
*Figure 4: $sqrt{I_D}$ vs VGS Characteristics for VGS=5V*
- For $V_{ds} = 0.1V$
![sqrtID vs VGS](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/TC(Vds%3D0.1V).png)
*Figure 5: $sqrt{I_D}$ vs VGS Characteristics for VGS=0.1V*
----
## Subthreshold Slope
![Subthreshold](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/log(Id).png)
*Figure 3: log(ID) vs VGS Graph*
---
----
#  Methodology

### Threshold Voltage Extraction
Using linear extrapolation from √ID vs VGS plot.

After Export data as text we get:
Taking the most linear region near threshold: (For VDS=5V)
| $V_{GS}(V)$ | $\sqrt{I_d}($\sqrt{A}$) |
|----------|--------|
| 2.5 | 0.01196101 |
| 3.0 | 0.02141756 |


- Then , $m = \frac{0.02141756}{0.01196101 }= 0.0189131 \frac{\sqrt{\mu A}}{V}$
- $V_{TH} = V_{GS} - \frac{\sqrt{I_d}}{m}  = 1.86V$
- 1.86V is very near to 2V.
-----
### gm Extraction
- $g_m = \frac{dI_D}{dV_{GS}}$ at $V_{GS}=3V$ is $g_m = 0.000709630839992S from simulation
![gm](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/gm.png)
- from theory, $g_m = \frac{2I_D}{V_{OV}} = 0.0009174234S$
- The simulated value is reduced due to : Mobility Degradation(THETA) , Short Channel Effect(DELTA) , Velocity Saturation(VMAX).
- ----

### Subthreshold Slope:
From Id vs VGS graph:
- $S = \frac{dV_{GS}}{d(log(I_{d}))} (mV/Decade)$
- At 300 K it's value is 60mV/Decade.
- Choose $V_{GS} = 1.5V to 1.8V$
- S = 122mV/Decade which is not equal to 60mV/Decade due to tap and bulk effects.
- --------

### gds Extraction:
From ID vs VDS graph for VGS = 3V , VDS = 5V
$g_{ds} = \frac{dI_D}{V_{DS}}$ = 1.01674231701e-05 S
![gds](https://github.com/Aditisarkar16122001/NMOS-Device-Characterization-and-Parameter-Extraction-for-Compact-Modeling/blob/main/gds.png)

--------

### $\lambda$ Extraction:
- at saturation ID = 0.0004587117 A, in ID vs VDS graph for VGS = 3V
- $\lambda = \frac{g_{ds}}{I_D} = 0.0221 V^{-1}$

------------
### Output Resistance

$r_o = \frac{1}{g_{ds}} = 98.7 K\ohm$

-------------
### DIBL Calculation

- $DIBL = \frac{\Delta V_{TH}}{\Delta V_{DS}}$
- Extracted value of $V_{th}$ for $V_{DS} = 0.1V$ as did for $V_{DS} = 5V$
- $V_{th}$ at $V_{DS}=5V$ is 1.86V, and $V_{th}$ at $V_{DS}=0.1V$ is 1.95V
- DIBL = 30 mV/V


---


##  Tools Used

- LTspice
- MOS Level 3 Model

---


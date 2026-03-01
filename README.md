
# NMOS Compact Modeling & Parameter Extraction using LTspice

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
| Threshold Voltage (Vth) | ~1.86 V | From √Id vs Vgs |
| gm | 7.09e-4 S | From slope at VGS = 3V |
| gds | Extracted | From Id–Vds slope |
| λ (Channel length modulation) | ~0.022 V⁻¹ | From saturation region |
| ro | ~98.7 kΩ | ro = 1/gds |
| Intrinsic Gain (gm·ro) | ~70 | Analog performance metric |
| Subthreshold slope | 122 mV/dec | Non-ideal behavior |
| DIBL | 30 mV/V | Short-channel effect |

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

##  Methodology

### Threshold Voltage Extraction
Using linear extrapolation from √ID vs VGS plot.

After Export data as text we get:
Taking the most linear region near threshold: (For VDS=5V)
| $V_{GS}(V)$ | $sqrt{I_d}(sqrt{A}$ |
|----------|--------|
| 2.5 | 0.01196101 |
| 3.0 | 0.02141756 |
Then , $m = \frac{(0.02141756}{0.01196101 }$ = 0.0189131 $\frac{\sqrt{\mu A}}{V}$
$V_{TH} = V_{GS} - \frac{sqrt{I_d}}{m}  = 

### gm Extraction
$g_m = \frac{dI_D}{dV_{GS}}$ at V


### Output Resistance
\[
r_o = \frac{1}{g_{ds}}
\]

### DIBL Calculation
\[
DIBL = \frac{\Delta V_{TH}}{\Delta V_{DS}}
\]

---


## 🛠 Tools Used

- LTspice
- MOS Level 3 Model
- Manual data extraction

---

## 📂 Repository Structure


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

## Model Card Used
.MODEL NMOS_L3 NMOS LEVEL = 3
+ TOX = 200E-10
+PHI = 0.7
+UO = 650
+KP = 120E-6
+RSH = 0
+XJ = 500E-9
+CGDO = 200E-12
+CJ = 400E-6
+CJSW = 300E-12
+NSUB = 1E17 VTO = 2 ETA = 3.0E-6 VMAX =1E5 NFS =1E12
+LD = 100E-9 CGSO=200E-12 PB=1 MJSW=0.5
+GAMMA=0  DELTA =3.0  THETA = 0.1
+KAPPA = 0.3  TPG=1  CGBO=1E-10 MJ=0.5

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

##  Key Graphs

### ID vs VDS
![ID vs VDS](graphs/id_vds.png)

### √ID vs VGS (Threshold Extraction)
![sqrtID vs VGS](graphs/sqrt_id_vs_vgs.png)

### Subthreshold Slope
![Subthreshold](graphs/subthreshold_slope.png)

---

##  Methodology

### Threshold Voltage Extraction
Using linear extrapolation from √ID vs VGS plot.

### gm Extraction
\[
g_m = \frac{dI_D}{dV_{GS}}
\]

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

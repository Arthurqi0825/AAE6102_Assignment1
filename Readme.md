# AAE6102 Assignment 1

## Satellite Communication and Navigation (2024/25 Semester 2)

### The Hong Kong Polytechnic University  
**Department of Aeronautical and Aviation Engineering**  

**Due Date:** 13 March 2025  

## Overview  
This assignment focuses on processing **GNSS Software-Defined Receiver (SDR) signals** to develop a deeper understanding of **GNSS signal processing**. Students will analyze **two real Intermediate Frequency (IF) datasets** collected in different environments: **open-sky** and **urban**. The urban dataset contains **multipath and non-line-of-sight (NLOS) effects**, which can degrade positioning accuracy.

### Dataset Information  

| Environment | Carrier Frequency | IF Frequency | Sampling Frequency | Data Format | Ground Truth Coordinates | Data Length | Collection Date (UTC) |
|------------|------------------|--------------|-------------------|------------|-----------------------|------------|-----------------|
| Open-Sky  | 1575.42 MHz | 4.58 MHz | 58 MHz | 8-bit I/Q samples | (22.328444770087565, 114.1713630049711) | 90 seconds | 14/10/2021 12.21pm|
| Urban     | 1575.42 MHz | 0 MHz | 26 MHz | 8-bit I/Q samples | (22.3198722, 114.209101777778) | 90 seconds | 07/06/2019 04.49am |

![image](https://github.com/IPNL-POLYU/AAE6102-assignments/blob/main/Picture1.png)

## Assignment Tasks  

### **Task 1 – Acquisition**  
Process the **IF data** using a **GNSS SDR** and generate the initial acquisition results.

### **Task 2 – Tracking**  
Adapt the **tracking loop (DLL)** to generate **correlation plots** and analyze the tracking performance. Discuss the impact of urban interference on the correlation peaks. *(Multiple correlators must be implemented for plotting the correlation function.)*

### **Task 3 – Navigation Data Decoding**  
Decode the **navigation message** and extract key parameters, such as **ephemeris data**, for at least one satellite.

### **Task 4 – Position and Velocity Estimation**  
Using **pseudorange measurements** from tracking, implement the **Weighted Least Squares (WLS)** algorithm to compute the **user's position and velocity**.  
- Plot the user **position** and **velocity**.  
- Compare the results with the **ground truth**.  
- Discuss the impact of **multipath effects** on the WLS solution.

### **Task 5 – Kalman Filter-Based Positioning**  
Develop an **Extended Kalman Filter (EKF)** using **pseudorange and Doppler measurements** to estimate **user position and velocity**.

# Solution of Assignment

## Task 1

### OpenSky Solution
![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/OpenSky_Acq.jpg)
### Urban Solution
![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/Acq_Result_Urban.jpg)

Acquired Satelliites numbers:
| Urban  | OpenSky |
|--------|---------|
| 1      | 16      |
| 3      | 22      |
| 11     | 26      |
| 18     | 27      |
|        | 31      |
## Task 2


## Task 3
The detailed ephemeris data for the urban dataset is stored in the file `eph_urban.mat`.

The table below presents some of the factors: 
| No of PRN | C_ic | Omega_0 | C_is | i_0 | C_rc | Omega | OmegaDot | IODE_sf3 | iDot | idValid | weekNumber | T_GD | IODC | t_oc | TOW |
|-----------|------|---------|------|-----|------|-------|----------|----------|------|---------|------------|------|------|------|-----|
| 1         | -7.45058059692383e-08 | -3.10603580061844 | 1.60187482833862e-07 | 0.976127704025531 | 287.468750000000 | 0.711497598513721 | -8.16962601200124e-09 | 72 | -1.81078971237415e-10 | [2,0,3] | 1032 | 0 | 0 | 453600 |
| 3         | 1.11758708953857e-08 | -2.06417843827738 | 5.21540641784668e-08 | 0.962858745925880 | 160.312500000000 | 0.594974558438532 | -7.83246911092014e-09 | 72 | 4.81091467962126e-10 | [2,0,3] | 1032 | 0 | 0 | 453600 |
| 11        | -3.16649675369263e-07 | 2.72577037566571 | -1.32247805595398e-07 | 0.909806735685279 | 324.406250000000 | 1.89149296226273 | -9.30431613354220e-09 | 83 | 1.28576784310591e-11 | [2,0,3] | 1032 | 0 | 0 | 453600 |
| 18        | -2.53319740295410e-07 | 3.12182125430595 | 3.53902578353882e-08 | 0.954642600078998 | 280.156250000000 | 1.39301587576552 | -8.61071581373341e-09 | 56 | -1.61792453590826e-10 | [2,0,3] | 1032 | 0 | 0 | 453600 |

## Task 4 
Positon and velocity estimation 

### OpenSky
![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/Position_OpenSky.jpg)

### Urban
![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/Position_urban.jpg)

### Comparision with Ground Truth
![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/OpenSky.png)

![image](https://github.com/Arthurqi0825/AAE6102_Assignment1/blob/main/Figures/urban.png)


## Task 5

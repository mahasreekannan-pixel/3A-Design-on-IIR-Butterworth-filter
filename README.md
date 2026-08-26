# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
clc; 
clear; 
close; 
// Input specifications 
wp = input('Enter the pass band frequency (Radians)= '); 
ws = input('Enter the stop band frequency (Radians)= '); 
alphap = input('Enter the pass band attenuation (dB)= '); 
alphas = input('Enter the stop band attenuation (dB)= '); 
T = input('Enter the sampling time = '); 
// Convert digital frequencies to analog frequencies
omegap = wp/T; 
disp(omegap,'omegap='); 
omegas = ws/T; 
disp(omegas,'omegas=');
 // Calculate filter order 
N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N = ceil(N); 
disp(N,'Rounded value of N='); 
// Cutoff frequency 
omegac = omegap/((10^(0.1*alphap)-1)^(1/(2*N))); 
disp(omegac,'omegac=');
 // Normalized Analog LPF 
disp('Normalized Analog LPF Transfer Function H(s)'); 
Hs_normal = analpf(N,'butt',[0,0],1); 
disp(Hs_normal); 
// Analog Butterworth LPF
 disp('Analog LPF Transfer Function H(s)'); 
Hs = analpf(N,'butt',[0,0],omegac); 
disp(Hs); 
// Impulse Invariant Transformation 
Hz = dscr(Hs,T); 
disp('Digital LPF Transfer Function H(z)'); 
disp(Hz);
 // Frequency response 
HW = frmag(Hz,512);
 w = 0:%pi/511:%pi; 
plot(w/%pi,abs(HW)); 
xlabel('Normalized Digital Frequency'); 
ylabel('Magnitude');
title('Frequency Response of Butterworth IIR LPF using Impulse Invariant Method');


# OUTPUT: 
<img width="530" height="232" alt="image" src="https://github.com/user-attachments/assets/dc781a2b-b5ca-44c7-aa3b-2595af9b857f" />
<img width="410" height="371" alt="image" src="https://github.com/user-attachments/assets/9701f311-6506-4a9f-8ef0-9cfad4028307" />
<img width="458" height="370" alt="image" src="https://github.com/user-attachments/assets/1aa69229-7a0d-4efe-a005-35fe2e1c87f7" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.


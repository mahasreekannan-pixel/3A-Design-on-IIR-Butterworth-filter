# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
<br>clc; 
<br>clear; 
<br>close; 
<br>// Input specifications 
<br>wp = input('Enter the pass band frequency (Radians)= '); 
<br>ws = input('Enter the stop band frequency (Radians)= '); 
<br>alphap = input('Enter the pass band attenuation (dB)= '); 
<br>alphas = input('Enter the stop band attenuation (dB)= '); 
<br>T = input('Enter the sampling time = '); 
<br>// Convert digital frequencies to analog frequencies
<br>omegap = wp/T; 
<br>disp(omegap,'omegap='); 
<br>omegas = ws/T; 
<br>disp(omegas,'omegas=');
<br> // Calculate filter order 
<br>N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
<br>disp(N,'N='); 
<br>N = ceil(N); 
<br>disp(N,'Rounded value of N='); 
<br>// Cutoff frequency 
<br>omegac = omegap/((10^(0.1*alphap)-1)^(1/(2*N))); 
<br>disp(omegac,'omegac=');
<br> // Normalized Analog LPF 
<br>disp('Normalized Analog LPF Transfer Function H(s)'); 
<br>Hs_normal = analpf(N,'butt',[0,0],1); 
<br>disp(Hs_normal); 
<br>// Analog Butterworth LPF
<br> disp('Analog LPF Transfer Function H(s)'); 
<br>Hs = analpf(N,'butt',[0,0],omegac); 
<br>disp(Hs); 
<br>// Impulse Invariant Transformation 
<br>Hz = dscr(Hs,T); 
<br>disp('Digital LPF Transfer Function H(z)'); 
<br>disp(Hz);
<br> // Frequency response 
<br>HW = frmag(Hz,512);
<br> w = 0:%pi/511:%pi; 
<br>plot(w/%pi,abs(HW)); 
<br>xlabel('Normalized Digital Frequency'); 
<br>ylabel('Magnitude');
<br>title('Frequency Response of Butterworth IIR LPF using Impulse Invariant Method');


# OUTPUT: 
<img width="530" height="232" alt="image" src="https://github.com/user-attachments/assets/dc781a2b-b5ca-44c7-aa3b-2595af9b857f" />
<img width="410" height="371" alt="image" src="https://github.com/user-attachments/assets/9701f311-6506-4a9f-8ef0-9cfad4028307" />
<img width="458" height="370" alt="image" src="https://github.com/user-attachments/assets/1aa69229-7a0d-4efe-a005-35fe2e1c87f7" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.


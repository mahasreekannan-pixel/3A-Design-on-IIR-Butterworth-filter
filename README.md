# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
# Impulse Invariant Program :
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

# Bilinear Program :
<br>clc ;
<br>close ;
<br>wp=input('Enter the pass band frequency (Radians )= ' );
<br>ws=input('Enter the stop band frequency (Radians )= ' );
<br>alphap=input( ' Enter the pass band attenuation (dB)=' );
<br>alphas=input( ' Enter the stop band attenuation(dB)=' );
<br>T=input('Enter the Value of sampling Time=');
<br>//Pre warping- Bilinear Transformation
<br>omegap=(2/T)*tan(wp/2);
<br>disp(omegap,'omegap=');
<br>=(2/T)*tan(ws/2);
<br>disp(omegas,'omegas=');
<br>//Order of the filter
<br>N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
<br>disp(N,'N=');
<br>N=ceil(N);
<br>disp(N,'Round off value of N=');
<br>//Cut off frequency
<br>omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));
<br>disp(omegac,'omegac=');
<br>disp('Normalised Analog LPF Transfer function H(S)=');
<br>hs_Normalised = analpf(N,'butt',[0,0],1);
<br>disp(hs_Normalised);
<br>disp('Analog LPF Transfer function H(S)=');
<br>hs= analpf(N,'butt',[0,0],omegac);
<br>disp(hs);
<br>z=poly(0,'z');//Defining variable z
<br>Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
<br>disp('Digital LPF Transfer function H(Z)=');
<br>disp(Hz);
<br>HW=frmag(Hz,512); // Frequency response
<br>w=0:%pi/511:%pi ;
<br>plot(w/%pi,abs(HW));
<br>xlabel(' Normalized Digital Frequency w');
<br>ylabel('Magnitude ');
<br>title(' Frequency Response of Butterworth IIR LPF');

# Manual Calculation :
# Impulse Invariant :
<img width="901" height="1509" alt="image" src="https://github.com/user-attachments/assets/13516452-153b-41e4-ab1c-bc9299c7c31c" />
<img width="1002" height="1563" alt="image" src="https://github.com/user-attachments/assets/48b6f31f-f245-482b-a0b0-d6498a06be34" />
<img width="954" height="1504" alt="image" src="https://github.com/user-attachments/assets/d1f569bf-06cd-4fdf-83db-dc34e86c4595" />

# Bilinear :
<img width="840" height="1512" alt="image" src="https://github.com/user-attachments/assets/9eeef3b7-8681-4f7f-9331-551471cdbbc3" />
<img width="948" height="1599" alt="image" src="https://github.com/user-attachments/assets/7c89a4c9-f40f-44a6-95ff-ea4b5c887f65" />
<img width="965" height="1600" alt="image" src="https://github.com/user-attachments/assets/0a64e7cf-363c-48bf-a1dc-672a947702e8" />



# OUTPUT: 
# Impulse Invariant :
<img width="530" height="232" alt="image" src="https://github.com/user-attachments/assets/dc781a2b-b5ca-44c7-aa3b-2595af9b857f" />
<img width="410" height="371" alt="image" src="https://github.com/user-attachments/assets/9701f311-6506-4a9f-8ef0-9cfad4028307" />
<img width="458" height="370" alt="image" src="https://github.com/user-attachments/assets/1aa69229-7a0d-4efe-a005-35fe2e1c87f7" />

# Bilinear :
<img width="526" height="234" alt="image" src="https://github.com/user-attachments/assets/8605b0eb-8aa5-4e91-a3d3-6fb37b1a5e4b" />
<img width="356" height="317" alt="image" src="https://github.com/user-attachments/assets/c70a2c54-1fe9-48bb-9767-2ec644d8e90f" />
<img width="454" height="373" alt="image" src="https://github.com/user-attachments/assets/cd9a2ea9-1614-4a15-b798-074cd71638d9" />


# RESULT: 
Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.



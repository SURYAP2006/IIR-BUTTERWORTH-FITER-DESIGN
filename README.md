# EXP 3 : IIR-BUTTERWORTH-FITER-DESIGN

## AIM: 

 To design an IIR Butterworth filter  using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (LPF): 
```
clc ;  

close ;  

wp=input('Enter the pass band frequency (Radians )= ' );  

ws=input('Enter the stop band frequency (Radians )= ' );  

alphap=input( ' Enter the pass band attenuation (dB)=' );  

alphas=input( ' Enter the stop band attenuation(dB)=' );  

T=input('Enter the Value of sampling Time=');  

omegap=(2/T)*tan(wp/2);  

disp(omegap,'omegap=');  

omegas=(2/T)*tan(ws/2);  

disp(omegas,'omegas=');    

N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));  

disp(N,'N='); 

N=ceil(N);  

disp(N,'Round off value of N=');  

omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));  

disp(omegac,'omegac=');  

disp('Normalised Analog LPF Transfer function H(S)=');  

hs_Normalised = analpf(N,'butt',[0,0],1);  

disp(hs_Normalised);  

disp('Analog LPF Transfer function H(S)=');  

hs= analpf(N,'butt',[0,0],omegac);  

disp(hs);  

z=poly(0,'z'); 

Hz=horner(hs,(2/ T)*((z -1)/(z+1))) 

disp('Digital LPF Transfer function H(Z)=');  

disp(Hz);  

HW=frmag(Hz,512);  

w=0:%pi/511:%pi ;  

plot(w/%pi,abs(HW));  

xlabel(' Normalized Digital Frequency w');  

ylabel('Magnitude '); 

title(' Frequency Response of Butterworth IIR LPF');

```


## PROGRAM (HPF): 



## OUTPUT (LPF) : 
<img width="1920" height="1080" alt="Screenshot 2025-09-22 152353" src="https://github.com/user-attachments/assets/24ecd1b6-2238-40af-82f1-b92afd2a2571" />


## OUTPUT (HPF) : 

## RESULT: 

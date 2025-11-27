# Frequency-Division-Multiplexing (FDM)

# AIM
To simulate Frequency Division Multiplexing (FDM) using Scilab and observe the multiplexing and demultiplexing of multiple message signals transmitted over different carrier frequencies.

# APPARATUS REQUIRED
A computer system

Scilab (Latest stable version)

Signal Processing Toolbox (inbuilt functions)

# THEORY
Frequency Division Multiplexing is a technique in which multiple message signals are transmitted simultaneously over a communication channel by allocating different carrier frequencies to each signal. Each signal modulates its own carrier → modulated signals are added → transmitted together → separated at the receiver using band-pass filters or carrier synchronization.


# ALGORITHM

Start Scilab.

Define simulation parameters:

Time vector

Carrier frequencies

Amplitude values

Generate two or more message signals (e.g., sine waves).

Generate carrier signals corresponding to each message.

Modulate each message using

<img width="314" height="50" alt="image" src="https://github.com/user-attachments/assets/9614ef10-e94a-4c6c-8332-d2b4f9e21c82" />

Add all modulated signals to obtain FDM signal.

Plot: - Message signals - Carrier signals - Individual modulated signals - Final FDM signal 

Multiply FDM signal with each respective carrier. 

Apply a Low-Pass Filter (LPF) to retrieve the baseband message. 

Plot the recovered signals. 11. End.


# Program

clc; 

clear; 

close;

fs = 50000;

t = 0:1/fs:0.05;

m1 = 3.5*sin(2*%pi*307*t);

m2 = 3.6*sin(2*%pi*317*t);

m3 = 3.7*sin(2*%pi*327*t);

m4 = 3.8*sin(2*%pi*327*t);

m5 = 3.9*sin(2*%pi*347*t);

m6 = 4.0*sin(2*%pi*357*t);

c1 = cos(2*%pi*2000*t);

c2 = cos(2*%pi*4000*t);

c3 = cos(2*%pi*6000*t);

c4 = cos(2*%pi*8000*t);

c5 = cos(2*%pi*10000*t);

c6 = cos(2*%pi*12000*t);

s1 = m1 .* c1;

s2 = m2 .* c2;

s3 = m3 .* c3;

s4 = m4 .* c4;

s5 = m5 .* c5;

s6 = m6 .* c6;

fdm = s1 + s2 + s3 + s4 + s5 + s6;

r1 = fdm .* c1;

r2 = fdm .* c2;

r3 = fdm .* c3;

r4 = fdm .* c4;

r5 = fdm .* c5;

r6 = fdm .* c6;


cutoff_hz = 400;

norm_cutoff = cutoff_hz/(fs/2);

M = 101; 

[h, w] = wfir('lp', M, [norm_cutoff, 0], 'hm', 0);  

d1 = conv(r1, h, 'same');

d2 = conv(r2, h, 'same');

d3 = conv(r3, h, 'same');

d4 = conv(r4, h, 'same');

d5 = conv(r5, h, 'same');

d6 = conv(r6, h, 'same');

d1 = 2 * d1;

d2 = 2 * d2;

d3 = 2 * d3;

d4 = 2 * d4;

d5 = 2 * d5;

d6 = 2 * d6;

figure(1);

subplot(3,2,1); plot(t,m1); title("Message 1");

subplot(3,2,2); plot(t,m2); title("Message 2");

subplot(3,2,3); plot(t,m3); title("Message 3");

subplot(3,2,4); plot(t,m4); title("Message 4");

subplot(3,2,5); plot(t,m5); title("Message 5");

subplot(3,2,6); plot(t,m6); title("Message 6");


figure(2);

plot(t,fdm); title("Multiplexed FDM");

figure(3);

subplot(3,2,1); plot(t,d1); title("Demod 1");

subplot(3,2,2); plot(t,d2); title("Demod 2");

subplot(3,2,3); plot(t,d3); title("Demod 3");

subplot(3,2,4); plot(t,d4); title("Demod 4");

subplot(3,2,5); plot(t,d5); title("Demod 5");

subplot(3,2,6); plot(t,d6); title("Demod 6");


# OUTPUT

![WhatsApp Image 2025-11-27 at 08 47 23_8e8d338c](https://github.com/user-attachments/assets/76d94892-3765-45bc-8aea-f785bfb7335e)

![WhatsApp Image 2025-11-27 at 08 47 48_90b0210b](https://github.com/user-attachments/assets/73905c6e-a49c-4e2f-849c-0df3aba5bc05)

![WhatsApp Image 2025-11-27 at 08 50 25_c731f388](https://github.com/user-attachments/assets/7720bca0-9e79-46b2-8bf6-b2b966cfa1dd)


# TABULATION

![WhatsApp Image 2025-11-27 at 18 42 45_da322aa1](https://github.com/user-attachments/assets/9497885b-2d15-464a-b237-1e01fe390a18)

![WhatsApp Image 2025-11-27 at 18 43 04_50ddb335](https://github.com/user-attachments/assets/0734c863-e5b4-4d10-b204-4770c80162e0)

# RESULT
Frequency Division Multiplexing (FDM) using Scilab and observe the multiplexing and demultiplexing of multiple message signals transmitted over different carrier frequencies is stimulated.

# Week 01 — Communication & Signal Fundamentals

The first week focuses on the foundations of digital communication and signal processing.

The goal is to understand how a signal is represented, sampled, filtered, modulated and transmitted through a noisy channel.

## Topics

* Frequency, amplitude, phase and bandwidth
* Time domain vs frequency domain
* FFT
* Sampling and aliasing
* Analog & digital modulation
* FSK / BPSK
* Frequency hopping
* Noise and SNR
* Shannon channel capacity
* Digital filtering
* Correlation / matched-filter concept
* Basic communication system

## Experiments

| Day | Topic               | Main Experiment                                |
| --- | ------------------- | ---------------------------------------------- |
| 01  | Signals & Frequency | Time-domain and FFT analysis                   |
| 02  | Sampling            | Nyquist theorem & aliasing                     |
| 03  | Modulation + FHSS   | FSK/BPSK and frequency hopping                 |
| 04  | Noise & SNR         | AWGN and SNR experiments                       |
| 05  | Filters             | Digital band-pass filtering                    |
| 06  | Communication Chain | BPSK + noise + correlation + simple encryption |

## Week 01 Communication Chain

```text
Data
 ↓
Encryption
 ↓
Modulation
 ↓
Noisy Channel
 ↓
Filtering / Correlation
 ↓
Demodulation
 ↓
Decryption
 ↓
Recovered Data
```

## Tools

* Python
* NumPy
* SciPy
* Matplotlib

## Key Takeaways

This week established the basic relationship between:

**signal → spectrum → sampling → modulation → channel → noise → detection → recovered information**

The experiments also showed why synchronization, filtering, channel coding and signal detection become important as communication systems become more complex.
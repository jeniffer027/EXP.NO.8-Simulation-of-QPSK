EXP.NO.8-Simulation-of-QPSK

8.Simulation of QPSK

AIM

To simulate Quadrature Phase Shift Keying (QPSK) modulation using Python and visualize its in-phase, quadrature, and resultant waveforms.

SOFTWARE REQUIRED

Google Colab or Jupyter Notebook

 Python 3.x
 
 Required Libraries: numpy, matplotlib

 ALGORITHMS

 1. Import required libraries.
 
 2. Define simulation parameters (symbol period, sampling frequency, etc.).
 
 3. Generate a random bit sequence.
 
 4. Map bits into QPSK symbols (2 bits per symbol).
 
 5. Assign each symbol a phase from the QPSK constellation.
 
 6. Generate QPSK-modulated waveform using cosine and sine for I/Q components.
 
 7. Plot:-In-phase component-Quadrature component-Resultant waveform.

PROGRAM
 
 # Import necessary libraries
 
 import numpy as np
 
 import matplotlib.pyplot as plt
 
 # Parameters
 
 num_symbols = 10             

T = 1.0                      

fs = 100.0                   

t = np.arange(0, T, 1/fs)    

# Number of QPSK symbols

 # Symbol period (seconds)
 
 # Sampling frequency (Hz)
 
 # Time vector for one symbol
 
 # Generate random bit sequence
 
 bits = np.random.randint(0, 2, num_symbols * 2)  # Two bits per symbol
 
 symbols = 2 * bits[0::2] + bits[1::2]            

# Initialize QPSK signal

 qpsk_signal = np.array([])
 
 symbol_times = []
 
 # Define phase mapping for QPSK (Gray Coding)
 
 symbol_phases = {
 
 0: 0,
 
 1: np.pi / 2,
 
 2: np.pi,
 
 3: 3 * np.pi / 2
 }
 
 # Map bits to symbol (0 to 3)
 
 # Generate the QPSK modulated signal
 
 for i, symbol in enumerate(symbols):
 
 phase = symbol_phases[symbol]
 
 symbol_time = i * T
 
 
 qpsk_segment = np.cos(2 * np.pi * t / T + phase) + 1j * np.sin(2 * np.pi * qpsk_signal = np.concatenate((qpsk_signal, qpsk_segment))
 
 symbol_times.append(symbol_time)
 
 # Full time vector
 
 t_total = np.arange(0, num_symbols * T, 1/fs)
 
 # Plotting the QPSK signal
 
 plt.figure(figsize=(14, 12))
 
 # In-phase component
 
 plt.subplot(3, 1, 1)
 
 plt.plot(t_total, np.real(qpsk_signal), label='In-phase (I)', color='blue')
 
 for i, symbol_time in enumerate(symbol_times):
 
 plt.axvline(symbol_time, color='red', linestyle='--', linewidth=0.5)
 
 plt.text(symbol_time + T/4, 0, f'{symbols[i]:02b}', fontsize=12, color='bla
 
 plt.title('QPSK - In-phase Component')
 
 plt.xlabel('Time')
 
 plt.ylabel('Amplitude')
 
 plt.grid(True)
 
 plt.legend()
 
 # Quadrature component
 
 plt.subplot(3, 1, 2)
 
 plt.plot(t_total, np.imag(qpsk_signal), label='Quadrature (Q)', color='orange')
 
 for i, symbol_time in enumerate(symbol_times):
 
 plt.axvline(symbol_time, color='red', linestyle='--', linewidth=0.5)
 
 plt.text(symbol_time + T/4, 0, f'{symbols[i]:02b}', fontsize=12, color='bla
 
 plt.title('QPSK - Quadrature Component')
 
 plt.xlabel('Time')
 
 plt.ylabel('Amplitude')
 
 plt.grid(True)
 
 plt.legend()
 
 # Resultant QPSK waveform
 
 plt.subplot(3, 1, 3)
 
 plt.plot(t_total, np.real(qpsk_signal), label='Resultant QPSK Waveform', color= for i, symbol_time in enumerate(symbol_times):
 
 plt.axvline(symbol_time, color='red', linestyle='--', linewidth=0.5)
 
 plt.text(symbol_time + T/4, 0, f'{symbols[i]:02b}', fontsize=12, color='bla
 
 plt.title('Resultant QPSK Waveform (Real Part)')
 
 plt.xlabel('Time')
 
 plt.ylabel('Amplitude')
 
 plt.grid(True)
 
 plt.legend()
 
 plt.tight_layout()
 
 plt.show()  
 
 OUTPUT
 
 ![image](https://github.com/user-attachments/assets/141a2310-29ca-46da-a399-f49533d2c1fc)
 
 RESULT / CONCLUSIONS
 
 The simulation successfully generated the QPSK modulated waveform. The in-phase and quadrature components were plotted, along with the resultant QPSK waveform.
The symbol transitions and binary mapping are clearly visualized.

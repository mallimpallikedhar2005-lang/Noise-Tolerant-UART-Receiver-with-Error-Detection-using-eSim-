**Noise-Tolerant UART Receiver with Gated Clock & Parity Check**

<img width="1123" height="794" alt="WhatsApp Image 2026-04-16 at 21 58 23" src="https://github.com/user-attachments/assets/aab012f3-f75f-45a3-b937-30771cda9c5a" />
<img width="1123" height="794" alt="WhatsApp Image 2026-04-16 at 21 58 23 (1)" src="https://github.com/user-attachments/assets/11a65931-062c-4635-af03-33281f154f26" />

This project implements a robust UART Receiver designed in eSim. It features a noise-filtering analog front-end and a precise digital control block that manages data synchronization and error detection.

**🚀 Key Features:**

**Mixed-Signal Design:** Integrates an analog recovery stage (LM741) with XSPICE digital logic.

**Gated Clock Control:** Uses an SR-Latch and Tristate Buffer to enable the local clock only during active transmission, saving power/simulation resources.

**"8+8" Pulse Logic:** Implements a timed counter to allow 8 pulses for data population and 8 pulses for data stability/obtaining.

**Hardware Error Detection:** A 7-bit + Parity XOR tree for real-time data integrity verification.

**Baud Rate:** Configured for 9600 bps (Bit period \approx 104.16\mu s).


**🛠️ Tools Used:**

**eSim:** Open-source EDA tool for mixed-signal simulation.

**KiCad:** Schematic capture.

**Ngspice:** Circuit simulation engine.

**XSPICE:** For digital primitive modeling (d_dff, d_srlatch, etc.).


**📁 Project Structure:**

**/Schematic:** KiCad schematic files and PDF export.

**/Netlist:** The .cir ngspice netlist for replication.

**/Waveforms:** Screenshots of transient analysis showing gated clock and parallel data output.


**📝 Working Principle:**

Start Bit Detection: An inverted Recovered_Tx signal sets the SR-Latch.
Clock Activation: The SR-Latch enables the Tristate Buffer, releasing the 9600Hz clock to the shift register.
Data Shifting: Serial data is latched into 8 D-Flip Flops.
Automatic Reset: A secondary VPULSE or Counter triggers the SR-Latch Reset after exactly 16 clock cycles, stopping the simulation and holding the data for plotting.


**📊 Results:**

The simulation confirms successful serial-to-parallel conversion. The gated clock activates on the Start Bit and shuts down precisely after the parity bit is stable, ensuring a clean "Buffer to Plot" result.


**🎓 Acknowledgments:**

Developed as part of the FOSSEE eSim Summer Fellowship 2026 selection task. Special thanks to the FOSSEE team at IIT Bombay for providing the eSim platform.


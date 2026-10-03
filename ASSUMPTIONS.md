# BMS Engineering & Design Assumptions

1. **Cell Configuration:** Default system configured for a 4S LiFePO4 / Li-ion battery pack ($N=4$). Firmware scales up to 16S via template parameter `BMS::Engine<16>`.
2. **Nominal Cell Voltage:** Nominal voltage assumed at $3300\text{ mV}$ per cell; maximum threshold set to $4200\text{ mV}$; minimum cutoff set to $2800\text{ mV}$.
3. **Hardware Platform:** Microcontroller platform is an ESP32 dual-core module operating at $240\text{ MHz}$ with hardware FPU.
4. **Task Execution Frequencies:**
   - Real-Time Safety & Diagnostics Loop: $20\text{ Hz}$ ($50\text{ ms}$ interval).
   - Differential Virtual Display Loop: $10\text{ Hz}$ ($100\text{ ms}$ interval).
   - Telemetry & Analytics Update Loop: $1\text{ Hz}$ ($1000\text{ ms}$ interval).
5. **Network Connectivity:** IoT telemetry assumes 2.4 GHz Wi-Fi connectivity to Blynk Cloud servers. Offline buffering handles temporary outages up to 32 events.
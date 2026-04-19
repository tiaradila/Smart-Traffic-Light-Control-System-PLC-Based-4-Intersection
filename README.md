# Smart-Traffic-Light-Control-System-PLC-Based-4-Intersection
A PLC-based smart traffic light control system for a 4-intersection layout, programmed using ladder diagram logic on an Omron PLC via CX-Programmer. The system integrates real-time clock scheduling, emergency override, and automated condition-based switching. Simulated and validated using Factory I/O and monitored via an Output Control Panel (OCP).

# Features
1. 4-Intersection Control — Independent traffic light logic for Simpang 1–4, each with green,
2. yellow, and red signal outputs
3. Multi-phase Timer Sequencing — 8 cascaded 100ms timers (T0000–T0007) controlling phase transitions across all intersections
4. Real-Time Clock (RTC) Scheduling — System reads hour, minute, and day from the PLC's internal clock (A351–A354) and activates based on time conditions
5. Day-based Conditions — Active on Wednesday & Thursday (KONDISI1) and Monday (KONDISI2), each with specific time windows
6. Emergency Override — EMERGENCY input (I:0.02) immediately triggers a WARNING output and halts normal operation
7. No Right Turn / Don't Go This Way signals — Auxiliary output signals (Q:100.12, Q:100.13) activated during restricted conditions
8. HOLD/START/STOP logic — Latching start circuit with manual STOP and emergency reset

# System Logic Overview
START SYSTEM = System start/stop/hold and emergency detection
SIMPANG 1-4 = Traffic light logic per intersection (green, yellow, red)
TIMER LAMPU SIMPANG 4 = Centralized timer chain for phase sequencing
TEAL TIME CLOCK = RTC reading — extracts seconds, minutes, hours, and day
KONDISI SETIAP RABU DAN KAMIS = Activates KONDISI1 on Wed/Thu within a defined time window
KONDISI MINGGU — SENIN = Activates KONDISI2 on Mon within a defined time window

# I/O Address Map
DIGITAL INPUTS
I:0.00 = START (System start button)
I:0.01 = STOP (System stop button)
I:0.02 = EMERGENCY (Emergency override input)

Internal Relays (Work Bits)
W0.00 = HOLD (Latching relay for start circuit)
W0.01 = MAIN (Main system active flag)
W0.02 = KONDISI1 (Active on Wednesday & Thursday, time-based)
W0.03 = KONDISI2 (Active on Monday, time-based)
W0.04 = DUMMY (Auxiliary internal relay)

OUTPUTS
Q:100.00 = HIJAU1 (Simpang 1 — Green)
Q:100.01 = KUNING1 (Simpang 1 — Yellow)
Q:100.02 = MERAH1 (Simpang 1 — Red)
Q:100.03 = HIJAU2 (Simpang 2 — Green)
Q:100.04 = KUNING2 (Simpang 2 — Yellow)
Q:100.05 = MERAH2 (Simpang 2 — Red)
Q:100.06 = HIJAU3 (Simpang 3 — Green)
Q:100.07 = KUNING3 (Simpang 3 — Yellow)
100.08 = MERAH3 (Simpang 3 — Red)
100.09 = HIJAU4 (Simpang 4 — Green)
100.10 = KUNING4 (Simpang 4 — Yellow)
100.11 = MERAH4 (Simpang 4 — Red)
Q:100.12 = NO RIGHT TURN (Auxiliary — no right turn signal)
Q:100.13 = DONT GO THIS WAY (Auxiliary — road closed signal)
Q:101.00 = WARNING (Emergency warning output)


# TOOLS 
PLC: Omron (CX-Programmer)
Simulation: Factory I/O
Monitoring: Output Control Panel (OCP)
Programming Language: Ladder Diagram (LD)

This project was developed as part of an Industrial Automation course assignment. For educational purposes only.

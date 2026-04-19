# Smart-Traffic-Light-Control-System-PLC-Based-4-Intersection
A PLC-based smart traffic light control system for a 4-intersection layout, programmed using ladder diagram logic on an Omron PLC via CX-Programmer. The system integrates real-time clock scheduling, emergency override, and automated condition-based switching. Simulated and validated using Factory I/O and monitored via an Output Control Panel (OCP).
#Features
1. 4-Intersection Control — Independent traffic light logic for Simpang 1–4, each with green,
2. yellow, and red signal outputs
3. Multi-phase Timer Sequencing — 8 cascaded 100ms timers (T0000–T0007) controlling phase transitions across all intersections
4. Real-Time Clock (RTC) Scheduling — System reads hour, minute, and day from the PLC's internal clock (A351–A354) and activates based on time conditions
5. Day-based Conditions — Active on Wednesday & Thursday (KONDISI1) and Monday (KONDISI2), each with specific time windows
6. Emergency Override — EMERGENCY input (I:0.02) immediately triggers a WARNING output and halts normal operation
7. No Right Turn / Don't Go This Way signals — Auxiliary output signals (Q:100.12, Q:100.13) activated during restricted conditions
8. HOLD/START/STOP logic — Latching start circuit with manual STOP and emergency reset

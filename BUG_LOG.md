# BMS Firmware Development Bug Log

| Bug ID | Task | Issue Description | Root Cause | Resolution / Fix |
| :--- | :--- | :--- | :--- | :--- |
| **BUG-01** | Task 1 | Unterminated `#ifndef` header guard in `BmsEngine.hpp`. | Missing `#endif` at the end of the header file. | Appended `#endif // BMS_ENGINE_HPP` at line 142. |
| **BUG-02** | Task 5 | Network tasks blocking 20 Hz safety execution during Wi-Fi outages. | Synchronous `WiFi.begin()` calls hanging execution. | Refactored network layer into non-blocking FSM using `millis()` timers. |
| **BUG-03** | Task 5 | Historical offline queue flushing out of chronological order. | Incorrect head/tail index increment in `OfflineQueue`. | Replaced circular queue logic with FIFO modulo pointer increments. |
| **BUG-04** | Task 6 | Blynk Virtual Pins displaying `0.00` for Risk Score and SOH. | Analytics metrics updated after telemetry payload assembly. | Updated payload construction sequence to attach analytics before dispatch. |
| **BUG-05** | Task 6 | Task stack overflow crash on Core 1 when formatting strings. | `vSafetyTask` stack allocated at 4096 bytes was exhausted by `snprintf`. | Increased `vSafetyTask` stack allocation to 8192 bytes in `xTaskCreatePinnedToCore`. |
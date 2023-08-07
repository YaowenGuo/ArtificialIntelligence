# 嵌入式

Esp32 Software Dependency.


Std

```
                +-------------+
                | esp-idf-svc |
                +-------------+
                       |
                       |
      ┌----------------┬----------------┐
      |                |                |
      |         +-------------+         |
      |         | esp-idf-hal |         |
      |         +-------------+         |
      |                |                |
      |     ┌----------┴-----------┐    |
      |     |          |           |    |
+-------------+ +-------------+ +--------------+
| esp-idf-sys | | embedded-hal| | embedded-svc |
+-------------+ +-------------+ +--------------+
```


- IDF: IoT Development Framework
- hal: Hardware Abstraction Layer
- sys:
- svc:
- PCB:  Printed Circuit Board
- PSC: Peripheral Access Crates (PACs)
- SVD: System View Description (SVD) files
- BSC: Board Support Crate (BSC, also known as a Board Support Package or BSP). This provides yet another layer of abstraction and might, for example, provide an API to the various sensors and LEDs on that board - without the user necessarily needing to know which pins on your microcontroller are connected to those sensors or LEDs.
- embedded-hal: Rust 官方维护的 Hardware Layer 抽象层


- esp-rs/esp-idf-hal	An implementation of the embedded-hal and other traits using the esp-idf framework.
- esp-rs/esp-idf-svc	An implementation of embedded-svc using esp-idf drivers. (safe)
- esp-rs/esp-idf-sys	Rust bindings to the esp-idf development framework. Gives raw (unsafe) access to drivers, Wi-Fi and more.
- esp-rs/embedded-svc	Abstraction traits for embedded services. (WiFi, Network, Httpd, Logging, etc.)


esp32c3: A Peripheral Access Crate (PAC) for the ESP32-C3 from Espressif.

Registers and their fields on a device are described in System View Description (SVD) files. svd2rust is used to generate Peripheral Access Crates (PACs) from these SVD files. The PACs provide a thin wrapper over the various memory-mapped registers defined for the particular model of micro-controller you are using.





No_Std


+-------------+
| esp32c3-hal |
+-------------+
      |
      |
+-------------+       +--------------+
| embedded-hal|       | esp-println  |
+-------------+       +--------------+


esp32c3-hal: https://github.com/esp-rs/esp-hal

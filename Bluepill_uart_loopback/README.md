# Project Name

## 1. Overview
This project demonstrates UART communication using STM32F103 (Blue Pill) with HAL library in polling mode. The system echoes received data back to the sender.

---

## 2. Hardware Requirements
- MCU: STM32F103C8T6 (Blue Pill)
- Debugger: ST-Link V2
- UART1(PA10) <-> UART1(PA9)

---

## 3. Pin Configuration

| Peripheral | Pin | Function |
|------------|-----|----------|
| USART1 TX  | PA9 | Transmit |
| USART1 RX  | PA10 | Receive |

---

## 4. Clock Configuration
- HSI: 8 MHz
- System Clock: 8 MHz
- APB2: 8 MHz

---

## 5. Features
- UART communication via HAL (polling mode)
- Echo received data
- Simple loopback test support

---

## 6. Software Requirements
- STM32CubeIDE 2.1.1 or later
- STM32CubeMX version 6.17.0 or later
- STM32F1 HAL driver package

---

## 7. Project Structure
Core/
├── Inc/ # Header files
├── Src/ # Source files
Drivers/
├── STM32F1xx_HAL_Driver/
├── CMSIS/
.cproject
.project
.Bluepill_uart_loopback.ioc

---

## 8. How to Build
1. Open project in STM32CubeIDE
2. Click "Build Project"
3. Fix any missing dependencies if needed

---

## 9. How to Flash
- Use ST-Link debugger
- Configurate the debug configurations:
    1. Right click on project
    2. Debug as -> debug configurations
    3. Check the name of projec. If not exist click **New launch configuration**
    4. In tab **Debugger**
       + Change Debug probe to **ST-LINK (OpenOCD)**
       + Click **Show generator options...**
       + Change Reset mode to **Software system reset**
    5. Apply -> Debug
- Click "Debug" button in toolbar

---

## 10. Usage
1. Connect PA9 <-> PA10
2. Run debug and check the rxbuf array

---

## 11. Known Issues
- Polling mode may miss data at high baud rates
- The receive shif buffer have 8 bit width so can not receive more than 1 byte data at a time.

---

## 12. Author
Quang Le
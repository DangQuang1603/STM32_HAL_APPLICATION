# Bluepill UART Control LED

## 1. Overview
This project demonstrates UART command-based LED control on an STM32F103C8T6 (Blue Pill) using the STM32 HAL library. The firmware receives commands from a serial terminal, interprets them, and controls the onboard LED connected to PC13.

---

## 2. Hardware Requirements
- MCU: STM32F103C8T6 (Blue Pill)
- Debugger: ST-Link V2
- Serial terminal: PuTTY, Tera Term, STM32CubeIDE console, or any UART terminal
- USB-to-TTL adapter for UART communication

---

## 3. Pin Configuration

| Peripheral | Pin | Function |
|------------|-----|----------|
| USART1 TX  | PA9 | UART transmit |
| USART1 RX  | PA10 | UART receive |
| LED        | PC13 | Onboard user LED |

---

## 4. Clock Configuration
- HSI: 8 MHz
- System Clock: 8 MHz
- APB2: 8 MHz

---

## 5. Features
- UART communication using HAL
- Interrupt-driven UART reception via HAL_UART_Receive_IT
- Command-based LED control
- Supported commands:
  - ON: turn on LED
  - OFF: turn off LED
  - EXIT: close the application
- Serial menu displayed on startup for user interaction

---

## 6. Software Requirements
- STM32CubeIDE 2.1.1 or later
- STM32CubeMX version 6.17.0 or later
- STM32F1 HAL driver package

---

## 7. Project Structure
Core/
  ├── Inc/      # Header files
  └── Src/      # main.c and HAL initialization code
Drivers/
  ├── STM32F1xx_HAL_Driver/
  └── CMSIS/
.cproject
.project
.Bluepill_uart_control_led.ioc

---

## 8. How to Build
1. Open the project in STM32CubeIDE.
2. Select the project and click Build Project.
3. Resolve any missing dependencies if the environment requires it.

---

## 9. How to Flash
1. Connect the Blue Pill board using ST-Link V2.
2. Open the project in STM32CubeIDE.
3. Create or select a debug configuration.
4. Use ST-Link as the debug probe.
5. Click Debug to flash and run the firmware.

---

## 10. Usage
1. Connect the UART pins:
   - PA9 (TX) to RX of USB-to-TTL module
   - PA10 (RX) to TX of USB-to-TTL module
2. Open a serial terminal with the following settings:
   - Baud rate: 115200
   - Data bits: 8
   - Stop bits: 1
   - Parity: None
3. Reset the board and observe the startup message.
4. Type one of the following commands:
   - ON
   - OFF
   - EXIT
5. The onboard LED on PC13 will respond accordingly.

---

## 11. Notes on the Source Code
The main program in main.c uses:
- HAL_UART_Receive_IT to read incoming characters asynchronously
- A command buffer to store typed input
- A small command parser to interpret ON, OFF, and EXIT
- A loop in main() to update the LED state based on the received command

---

## 12. Known Issues
- The command parser currently accepts only simple uppercase commands.
- The UART input is handled as a line-based command, so the user must press Enter after typing a command.
- The application is intended for learning and demonstration purposes and may require further improvement for production use.

---

## 13. Author
Quang Le

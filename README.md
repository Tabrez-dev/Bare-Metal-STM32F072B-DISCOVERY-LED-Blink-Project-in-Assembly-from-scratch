# Bare Metal STM32F072B-DISCOVERY LED Blink Project

## Project Overview
This is a simple embedded project to blink **LED3** (PC6) on the **STM32F072B-DISCOVERY** board. The project demonstrates low-level GPIO configuration and LED control using assembly language.

## Hardware Used
- **STM32F072B-DISCOVERY** board
- **LED3** connected to **PC6**

## Prerequisites
- ARM GCC Toolchain
- OpenOCD
- Telnet client
- STM32F072B-DISCOVERY board

## Project Setup

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/STM32F072B_LED_Blink.git
cd STM32F072B_LED_Blink
```

### 2. Install Dependencies
```bash
# Install ARM GCC Toolchain
sudo apt-get install gcc-arm-none-eabi

# Install OpenOCD
sudo apt-get install openocd

# Install Telnet client
sudo apt-get install telnet
```

## Build Instructions
```bash
# Compile the project
make
```

## Flashing and Debugging with OpenOCD and Telnet

### Step 1: Start OpenOCD Server
Open a terminal and run:
```bash
openocd -f board/stm32f0discovery.cfg
```
This command initializes the OpenOCD server for the STM32F072B-DISCOVERY board. It sets up the debugging interface and prepares the board for programming.

### Step 2: Connect with Telnet
In a new terminal window, connect to the OpenOCD server:
```bash
telnet localhost 4444
```
Note: `4444` is the default OpenOCD telnet port.

### Step 3: Flash and Run the Firmware
Once in the telnet terminal, execute these commands:
```bash
# Reset the target and initialize
reset init

# Write the firmware image
flash write_image erase boot_up.elf

# Resume the target (start executing the code)
resume
```

#### Command Explanations:
- `reset init`: Resets the microcontroller and prepares it for programming
- `flash write_image erase boot_up.elf`: Erases the existing firmware and writes the new firmware image
- `resume`: Starts program execution after flashing

## Troubleshooting
- Ensure your STM32F072B-DISCOVERY board is properly connected
- Check that all dependencies are installed
- Verify the correct OpenOCD configuration file for your board

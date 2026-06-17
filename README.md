# Smart-alarm-clock-on-STM32F4-with-FreeRTOS
Đồng hồ báo thức đa chức năng trên STM32F411: phát nhạc MP3, hiển thị LEDmatrix phản ứng âm thanh và quản lý alarm profile tùy chỉnh hoàn toàn quaFreeRTOS.
STM32F4-FreeRTOS-Smart-Media-Clock
A RTC alarm clock built on STM32F411 using FreeRTOS. Features include an audio-reactive LED display, MP3 music playback, and fully customizable alarm profiles (tones & volume).

STM32F4 FreeRTOS Smart Media Clock
Project Status Platform OS

An advanced, feature-rich embedded clock system powered by the STM32F411CEU6 microcontroller and FreeRTOS. This project goes beyond a standard digital clock by integrating real-time audio processing for LED effects, media playback, and smart alarm management.

🌟 Key Features
Real-Time Accuracy: Displays highly accurate time and date using the DS1307 RTC module.
Audio-Reactive LED Effects: Uses an INMP441 I2S MEMS microphone to capture real-time audio and synchronizes it with WS2812 RGB LEDs for dynamic visual effects.
Smart Media Alarm: Features customizable alarm settings with high-quality MP3 playback via the DFPlayer Mini module.
Flash Memory Storage: Alarm configurations are safely stored in the MCU's internal Flash memory, ensuring data is retained even after power loss.
Intuitive UI: Clean and responsive user interface displayed on a 0.96-inch SSD1306 OLED screen.
Multitasking: Efficient task management and low-latency audio processing handled by FreeRTOS.
🛠️ Hardware Components
Component	Description	Protocol/Interface
STM32F411CEU6	Main Microcontroller (ARM Cortex-M4, 100MHz)	N/A
DS1307	Real-Time Clock (RTC) with backup battery	I2C
INMP441	Digital MEMS Microphone with built-in ADC	I2S + DMA
DFPlayer Mini	MP3 Audio Decoder & Amplifier	UART
SSD1306	0.96" OLED Display (128x64)	I2C
WS2812	Smart RGB LED Strip	PWM (Timer)
Mechanical Switches	User input for menu navigation and settings	EXTI
🧠 System Architecture (FreeRTOS)
The system relies on FreeRTOS (CMSIS_V2) to manage multiple tasks concurrently without blocking the audio processing pipeline.

I2S_ledTask (High Priority): Triggered by an I2S DMA interrupt. It reads digital audio samples from the INMP441, processes the amplitude, and updates the WS2812 LEDs to create synchronized lighting effects.
I2C_TimeTask (Normal Priority): Manages the user interface. It reads data from the RTC, updates the OLED display, and handles the state machine for menu navigation via EXTI button inputs.
I2C_Time_ClockTask (Low Priority): Continuously checks if the current RTC time matches the user-defined alarm. It triggers the DFPlayer and saves any user configuration changes to the Flash memory.
🚀 Getting Started
Prerequisites
STM32CubeIDE (Used for development and compilation)
ST-Link V2 (For programming and debugging)
Installation & Flashing
Clone this repository to your local machine.
Open the project folder in STM32CubeIDE.
Re-generate the initialization code via the .ioc file if necessary.
Build the project and flash it to the STM32F411CEU6 using your ST-Link.
📸 Demo
System Demo

👥 Authors
This project was developed as a coursework assignment for Embedded Systems at the Academy of Cryptography Techniques (KMA).

Hà Văn Đạt (DT060209)
Dương Hải Đăng (DT060206)
Nguyễn Mạnh Lân (DT060231)
Instructor: ThS. Lê Thị Hồng Vân

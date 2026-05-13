# EXPERIMENT-02-INTERFACING-A-DIGITAL-INPUT-OUTPUT-TO-IOT-DEVELOPMENT-BOARD


**DATE:22-04-26**

**NAME: Iniyasri S**

**ROLL NO:212223230081**

**DEPARTMENT:AIDS**

## Aim

To Interface a Digital Input (IR pair ) to ARM IOT development board and write a program to obtain the data

## Components required

- STM32 CUBE IDE
- ARM IOT development board
- STM programmer tool
- IR Pair Sensor

## Theory

The ARM (Advanced RISC Machine) architecture is widely used in microcontrollers and processors due to its efficiency, low power consumption, and high performance. ARM processors follow the Reduced Instruction Set Computing (RISC) design, making them ideal for embedded systems, mobile devices, and IoT applications. Many well-known semiconductor companies, including STMicroelectronics, use ARM-based architectures to develop powerful and energy-efficient microcontrollers.

One such microcontroller is the STM32WLE5JC, which is part of the STM32 family and is based on the ARM Cortex-M4 core. It is specifically designed for LoRaWAN® and other sub-GHz wireless communication applications, making it ideal for IoT and LPWAN (Low Power Wide Area Network) solutions. This microcontroller integrates a LoRa® transceiver, eliminating the need for an external radio module and reducing both cost and power consumption. With a maximum clock speed of 48 MHz, 256 KB of Flash memory, and 64 KB of RAM, it provides enough computing power for real-time data processing and wireless communication.

The STM32WLE5JC is known for its ultra-low power consumption, making it perfect for battery-operated IoT devices such as smart agriculture sensors, environmental monitoring systems, industrial automation, and asset tracking. It supports multiple communication interfaces, including I2C, SPI, and UART, allowing seamless integration with various sensors and peripherals. Additionally, it features built-in security capabilities such as AES 256-bit encryption and a True Random Number Generator (TRNG) for secure data transmission.

With its power-efficient design, built-in LoRaWAN support, and flexible communication options, the STM32WLE5JC is an excellent choice for developers looking to build long-range, low-power IoT applications. It is fully compatible with STM32CubeIDE and LoRaWAN middleware, making development and deployment easier for engineers and learners alike.

## IR PAIR

![image](https://github.com/user-attachments/assets/c0e0a1c8-b7be-4d10-9307-46432c31f26e)

IR technology is used in a wide range of wireless applications which includes remote controls and sensing. The infrared part in the electromagnetic spectrum can be separated into three main regions: near IR, mid-IR & far IR. The wavelengths of these three regions vary based on the application. For the near IR region, the wavelength ranges from 700 nm- 1400 nm, the wavelength of the mid-IR region ranges from 1400 nm – 3000 nm & finally for the far IR region, the wavelength ranges from 3000 nm – 1 mm.The near IR region is used on fiber optic & IR sensors, the mid-IR region is used for heat sensing and the far IR region is used in thermal imaging. The range of frequency for IR is maximum as compared to microwave and minimum than visible light.

## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   
<img width="1919" height="1199" alt="Screenshot 2026-05-01 134710" src="https://github.com/user-attachments/assets/7b5fd3d5-d18c-4807-9e6e-0fb9da0a3436" />



2. Click on FILE, click on new stm 32 project

<img width="1919" height="1199" alt="Screenshot 2026-05-01 134817" src="https://github.com/user-attachments/assets/34c7499c-92b8-4adc-a1b4-d1f95b2b102b" />
<img width="1919" height="1199" alt="Screenshot 2026-05-01 134943" src="https://github.com/user-attachments/assets/2f06d66b-8f3a-45c6-80db-bb2ff50ef29c" />


3. Select the target to be programmed as shown below and click on next

![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4. Select the program name

![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)

5. Corresponding ioc file will be generated automatically

![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)


6. Select the appropriate pins as GPIO, in or out, USART or required options and configure

![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)

![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)


7. Click on Ctrl+S, automatically C program will be generated

![Screenshot 2025-03-11 134709](https://github.com/user-attachments/assets/70b83b79-1569-4f14-99d5-e2adbb4e692d)

8. Edit the program and as per required 

<img width="1074" height="738" alt="image" src="https://github.com/user-attachments/assets/8e8663fc-97f5-4d1d-9fd4-a306490025e1" />



9. Use project and build all 

<img width="1910" height="1199" alt="image" src="https://github.com/user-attachments/assets/d9cc13ff-0c75-446d-a731-0d374e2d3cc6" />


10. Once the project is bulild 

<img width="717" height="264" alt="image" src="https://github.com/user-attachments/assets/0d7da003-4b2f-41e9-beef-e20640667dbc" />


11. connect the iot board to power supply and usb

12. After connecting open the STM cube programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)


13. Connect the STM board through the COM port, then upload the corresponding project ELF file/Hex file or Bin file in Erasing & Programming Window,while ensuring the board is in flash mode, and click on 'Start Program'.
    <img width="1600" height="859" alt="WhatsApp Image 2026-05-01 at 2 04 11 PM" src="https://github.com/user-attachments/assets/d6a6ed88-8382-4d66-910a-9abf3ce50c98" />


14.  After the file download is complete, switch your board to run mode and press the reset button to see the output


## STM 32 CUBE PROGRAM

```
#include "main.h"
#include "stdbool.h"
bool IRSENSOR;
void IRPAIR();
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
while (1)
  {
    IRPAIR();
}
void IRPAIR()
{
	IRSENSOR=HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_4);
	if(IRSENSOR==0){
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
		HAL_Delay(1000);
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		HAL_Delay(1000);
	}
	else{
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		HAL_Delay(1000);
	}
}
```

## OUTPUT
<img width="900" height="1600" alt="WhatsApp Image 2026-05-01 at 2 19 41 PM" src="https://github.com/user-attachments/assets/df304fe4-c26e-49ba-802f-8b8681715f51" />
<img width="900" height="1600" alt="WhatsApp Image 2026-05-01 at 2 19 41 PM (1)" src="https://github.com/user-attachments/assets/5d944a54-10ff-4aa1-9bca-a6351d634549" />



## Result

Interfacing a digital Input (ir pair) with ARM microcontroller based IOT development is executed and the results are verified.

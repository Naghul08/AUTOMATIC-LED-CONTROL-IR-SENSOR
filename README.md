# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/6304ac81-452e-4be3-b3e6-84b2fb41befc" />


2. Click **File → New STM32 Project**.
<img width="1918" height="1198" alt="image" src="https://github.com/user-attachments/assets/97254480-1e3a-4a64-9577-a95b5448f8e3" />
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/150738c4-5aa7-453d-80c0-43277cb1eb2a" />

3. Select the **target microcontroller** or board and click **Next**.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/7cd0ebf2-b1ad-4f7f-a3c4-f3884216fe03" />

4. Name the project.

<img width="586" height="654" alt="image" src="https://github.com/user-attachments/assets/8d7032ad-1009-4236-a961-cd858fe94fd1" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="1704" height="1023" alt="image" src="https://github.com/user-attachments/assets/dafdb2c7-2d97-41b1-848a-bf9266f8a608" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1702" height="1017" alt="image" src="https://github.com/user-attachments/assets/3af71561-b8d1-42da-bc30-941f17cc9027" />
<img width="1706" height="1016" alt="image" src="https://github.com/user-attachments/assets/604eb147-8725-465b-8923-0dc568785bca" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1706" height="1025" alt="image" src="https://github.com/user-attachments/assets/20dcfcd4-2c67-476b-9cfc-afca92389615" />
 
8. Edit the generated main program as required.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/575d0309-b8a3-43dd-827b-8bf45e0944bb" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/40b52f6a-e737-4d00-ab79-e5d10c7f312e" />

9. Click **Project → Build All**.
<img width="958" height="242" alt="image" src="https://github.com/user-attachments/assets/b84811c9-e421-40dc-ba65-1ce4ff707588" />

10. Link the **HEX file** using the post-build process.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/700c3102-157a-4324-a017-0b68cd4edd4a" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1914" height="1199" alt="image" src="https://github.com/user-attachments/assets/85697e72-7de7-480d-9965-2bd99cc68ded" />


13. Click **Run** to execute the program.
    
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

![WhatsApp Image 2025-11-06 at 20 20 37_eac079ca](https://github.com/user-attachments/assets/d23437af-486c-47fa-a610-24fe1549d3c2)

CASE 2: LED OFF

![WhatsApp Image 2025-11-06 at 20 20 35_64b6bcdb](https://github.com/user-attachments/assets/b9940c34-744b-41b5-a50e-153c028e23f4)


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




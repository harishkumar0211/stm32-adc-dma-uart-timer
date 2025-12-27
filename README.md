# STM32 Timer Triggered ADC with DMA and UART Output (NUCLEO-G070RB)

## 🎥 Demonstration Video
Video showing real-time ADC readings: https://drive.google.com/file/d/1g9BYNXiVou0dE_UMtcMdONdD1-M0B31x/view?usp=drivesdk


## 🔹 Project Objective
Acquire analog data at a stable 100 Hz sampling rate using:
- Hardware Timer Trigger (TIM3)
- ADC with DMA
- UART transmission to PC

This assignment was completed as part of an internship evaluation.

## 🔹 Hardware Used
- STM32 NUCLEO-G070RB
- B10K Linear Potentiometer
- USB connection via ST-LINK Virtual COM Port
- PC running PuTTY (115200 baud)

> STM32G070RB was used instead of Blackpill due to hardware availability.

## 🔹 System Block Diagram

```
TIM3 (100 Hz)
      ↓ TRGO
ADC1 (External Trigger)
      ↓
DMA (Circular Buffer)
      ↓ Interrupt
UART2 (115200 baud)
      ↓
PC Terminal (PuTTY)
```


## 🔹 Features
- Timer controls sampling frequency → precise 100 Hz
- ADC conversion triggered by hardware → no jitter
- DMA circular mode → continuous sampling without CPU load
- UART → live data streaming to PC terminal

## 🎛️ Potentiometer Test
Analog input pin: **PA0 (ADC Channel 0)**

| Pot Position | ADC Value (approx) |
|-------------|-------------------|
| Min (0V) | ~0 |
| Middle (1.65V) | ~2000 |
| Max (3.3V) | ~4095 |

📌 Real-time variation visible in serial output when rotating knob

## 🛠️ Software
- STM32CubeIDE
- HAL drivers
- DMA, Timer, ADC, UART properly configured in CubeMX

## 🧠 Technical Summary
- TIM3 configured for 100 Hz (Prescaler = 1599, Period = 99)
- ADC triggered by TIM3 TRGO on rising edge
- DMA moves ADC results to buffer automatically
- Callback sends values to UART once buffer is full

## 🏁 Conclusion
This project demonstrates efficient real-time data acquisition using:
✔ Hardware triggering  
✔ DMA optimization  
✔ Continuous UART streaming  
✔ Real analog input validation

Successfully completed and tested!

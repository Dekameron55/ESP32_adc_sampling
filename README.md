# ESP32_adc_sampling
ESP32 Demo application of ADC readouts which are then displyed on the oled ssd1307 display.

The application consists of mainly two tasks which run concurrently on one of the CPU cores.
After the initialization of the i2c, oled and ADC the two tasks begin executing.
First task is the ADC readout of the voltage drop on the potentiometer.
The ADC makes multisample readout and then averages it. The raw samples are then convereted into mV.
The raw values and values in mV are written in a freertos kernel type queue and after that the task is
put into a blocked state via vTaskDelay.

The second task begins to update the display. It begins by reading out the current value in the queue,
initializes the oled display and displays the value. After that the task enters a blocked state via vTaskDelay,
and the cycle repeats ones again with the first task.

![Screenshot]:(https://github.com/Dekameron55/ESP32_adc_sampling/blob/main/Picture1.png)

The example was ran on the wokwi simulator website.

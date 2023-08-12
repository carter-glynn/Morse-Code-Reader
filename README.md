# Traffic-Light-Controller

## Goal
 - Use FreeRTOS on the STM32 NUCLEO series to create an embedded system.
 - Read inputs received from external sources, interpret them in real time, and output the correct message.
 - Utilize OS functions such as Tasks, Semaphores, Queues, Interrupts, Scheduling, etc.

## Description

Create a Morse Code Reader using FreeRTOS on an embedded system using on-board buttons. Program the board to receive button presses, take in the length of signal, interpret the signal(s) and produce the correct message corresponding to the following chart: <br>

![Morse Code Chart](morse.png) <br>

The sender (user) will use the button to encode messages. <br>

### Tasks

Task 1

 - receive the button signal, convert it to dot or dash, then enqueue it to queue 1

Task 2

 - dequeue the dot or dash from queue 1, use an LED to show it, then enqueue it to another two queues (queue 2_1 and queue 2_2), in which all dots or dashes are saved. The LED should light simultaneously as you press the button

Task 3

 - dequeue the queue 2_1, whenever it found the newer dots or dashes can be decoded, it will decode it and print the corresponding letter (also simultaneously as you press the button)

Task 4

 - after input finishes, it will dequeue queue 2_2, and then light up another LED to show the whole sequence of the dots and dashes

## Definitions

Lenght of time needed to produce desired effect (in ms). <br>
(ex. to intput a new letter, one must wait 3 seconds after the last signal before the program will recognize a new letter is being inputted)

 - Dot Signal: 		1000
 - Dash Signal: 		3000
 - Same Letter Pause:		1000
 - Different Letter Pause: 		3000
 - Space Character		7000

---
title: "Low cost USBasp Programmer"
date: 2017-12-21T21:26:28+05:30
draft: false
---

To program any microcontroller, one needs a programmer. So my first project was making a programmer using USBasp proeject. It is an open source programmer, based on V-USB which allows Atmel AVR microcontrollers to be interfaced with a USB. Thats one great thing about AVRs. They are very well supported by open source tools. They also have really comprehensive datasheets. They are therefore a great choice for someone who is just starting out.

The chicken and egg problem of programming the microcontroller on the programmer was easily solved by hunting down the components of an old Compaq P – III in the basement. The computer had a parallel port, so the microcontroller on the usbasp could be programmed using AVRdude in DAPA mode – Direct AVR Parallel Access. Parallel ports disappeared, else they are do damn versatile!

First issue is that laptops often have only usb available to them. They lack any serial or parrallel port. USBasp is therefore a great programmer to use. It is very simple, once you learn how to solder components properly.

I became quite good at soldering, while making usbasp prototypes. I was trying to achieve as small a form factor as I could, with DIP components. I was quite satisfied with my third prototype that finally worked. It was quite small indeed! I also learnt the PCB routing software EAGLE and Dip Trace afterwards, while making a Custom PCB of this very programmer. It was fun when it all worked 🙂

I will be posting the pictures and videos once I can find them.

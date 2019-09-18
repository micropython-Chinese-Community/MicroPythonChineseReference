USB转串口
----------------------------------------

适合带有USB接口的STM32系统

 ::

    import pyb
    import select

    def pass_through(usb, uart):
        usb.setinterrupt(-1)
        while True:
            select.select([usb, uart], [], [])
            if usb.any():
                uart.write(usb.read(256))
            if uart.any():
                usb.write(uart.read(256))

    pass_through(pyb.USB_VCP(), pyb.UART(6, 115200, timeout=0))


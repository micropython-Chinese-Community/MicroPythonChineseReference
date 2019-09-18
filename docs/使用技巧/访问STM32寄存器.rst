访问STM32寄存器
----------------------------------------

在某些情况下，我们需要访问STM32内部的寄存器，执行某些micropython还没有提供的功能，或者是执行与固件不同的功能。

首先，需要import stm，通过stm模块就可以访问stm32内部的寄存器。如： ::

    stm.mem16[stm.GPIOA+stm.GPIO_BSRRH]| = 1<<1
    stm.mem16[stm.GPIOA+stm.GPIO_BSRRL]| = 1<<1

    stm.mem16[stm.GPIOC+stm.GPIO_BSRR] |= 1<<3
    stm.mem16[stm.GPIOC+stm.GPIO_BRR] |= 1<<3


stm模块的基本使用方式是： ::

    stm.mem8[REG + offser]
    stm.mem16[REG + offser]
    stm.mem32[REG + offser]


可以通过8/16/32位方式访问寄存器，通过寄存器名称（地址）加上偏移量访问，可以对寄存器读写和位操作。对于某些型号的stm32单片机，可能固件中没有提供寄存器名称，需要使用数字方式进行访问。

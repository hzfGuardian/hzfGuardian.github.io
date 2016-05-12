

## stm32 delay_$$\mu s$$函数实现

###感冒脑子烧糊涂了来发一发博

今年这个嵌入式啊好像对stm32这块市价只有七块钱的便宜货情有独钟啊，也难怪学会stm32的peek和poke都阔以火星救援了也是牛逼。人在头昏的时候容易装逼无止境，给DHT-11还要用stm32控制的忠实爱好者来一发stm32的微秒延时函数的实现，当然我也不是吃饱了撑的，DHT-11的握手协议强行要我一个微秒延时函数还一脸怪我咯的意思。

装逼第一点，首先我们要明确，这里使用stm32外部时钟HCLK，频率8MHz(调用`HAL_RCC_GetHCLKFreq`函数可以查到)，8分频，即1MHz。根据`SysTick`的工作原理，我们将`SysTick->LOAD`的初值设置为1000，就可以产生1ms的时基。原因是我们使用1M作为系统时钟，那么每次计数器减1所用的时间是1/1M，计数器的初值如果是1000，那么每次计数器减到0，时间经过(1/1M)*1000= 0.001s = 1ms，可以简单理解为：用1M的时钟频率，即1s计数1M=1000000次，那1ms计数1000次，所以计数初值为1000。

于是，一言不合就重写了一个毫秒延时的函数`delay_ms`：

	#include "stm32f1xx_hal.h"
	#include "Delay.h" 
	
	typedef unsigned char u8;
	typedef unsigned short u16;
	typedef unsigned int u32;
	
	void delay_ms(u16 nms)
	{
		SysTick->LOAD = (u32)nms * 1000; //给重装载寄存器赋值，1000时，将产生1ms的时基
		SysTick->CTRL |= 0x01;               //开始倒数
		while(!(SysTick->CTRL & (1<<16)));   //等待时间到达
		SysTick->CTRL = 0x00000000;         //关闭计数器
		SysTick->VAL = 0x00000000;          //清空计数器
	}


装逼第二点，就不用说了，把`SysTick->LOAD`的初值改为上面的千分之一，就是微秒延时函数`delay_ms`：

	void delay_us(u16 nms)
	{
		SysTick->LOAD = (u32)nms * 1; //给重装载寄存器赋值，1时，将产生1us的时基
		SysTick->CTRL |= 0x01;               //开始倒数
		while(!(SysTick->CTRL & (1<<16)));   //等待时间到达
		SysTick->CTRL = 0x00000000;         //关闭计数器
		SysTick->VAL = 0x00000000;          //清空计数器
	}

好了，溜。
uCOS+uCGUI 项目里面包括2个目标配置，第1个是定位地址0处，第2个是定位在地址0x40000处。

第2个可以和DfuSe升级Bootlo程序共存，实现在线升级功能。

修改定位地址的方法:
(1) 修改 fwlib\inc\stm32f10x_nvic.h
#if DEF_ROM_0X40000
#define NVIC_VectTab_FLASH           ((u32)0x08000000)
#else
#define NVIC_VectTab_FLASH           ((u32)0x08000000)
#endif

(2)在KEIL 工程选项里面，C++栏，增加 DEF_ROM_0X40000 宏。

问题1： 修改 fwlib\inc\stm32f10x_nvic.h 未起作用
KEIL 编译的时候找到KEIL目录下的库文件。原来是include路径为添加本地的fwlib\inc\文件夹

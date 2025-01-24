# UART设备

## 访问UART设备
通过IO设备的管理接口来访问串口硬件
```c
rt_device_t rt_device_find(const char* name);	//查找设备


rt_err_t rt_device_open(rt_device_t dev, rt_uint16_t oflags);	//打开设备
//////////////////////////////////
//oflag支持:
#define RT_DEVICE_FLAG_STREAM       0x040     // 流模式      
// 接收模式参数 
#define RT_DEVICE_FLAG_INT_RX       0x100     // 中断接收模式 
#define RT_DEVICE_FLAG_DMA_RX       0x200     // DMA 接收模式 
// 发送模式参数 
#define RT_DEVICE_FLAG_INT_TX       0x400     // 中断发送模式 
#define RT_DEVICE_FLAG_DMA_TX       0x800     // DMA 发送模式 

不指定参数则使用轮询模式

流模式：用于向串口终端输出字符串：当输出的字符是 "\n" （对应 16 进制值为 0x0A）时，自动在前面输出一个 "\r"（对应 16 进制值为 0x0D） 做分行。
///////////////////////////////

rt_device_read()	//读取数据

rt_device_write()	//写入数据

rt_device_control()	//控制设备
//////////////////////////////
默认配置
#define RT_SERIAL_CONFIG_DEFAULT           \
{                                          \
    BAUD_RATE_115200, /* 115200 bits/s */  \
    DATA_BITS_8,      /* 8 databits */     \
    STOP_BITS_1,      /* 1 stopbit */      \
    PARITY_NONE,      /* No parity  */     \
    BIT_ORDER_LSB,    /* LSB first sent */ \
    NRZ_NORMAL,       /* Normal mode */    \
    RT_SERIAL_RB_BUFSZ, /* Buffer size */  \
    0                                      \
}
/////////////////////////////

rt_device_set_rx_indicate()	//设置接收回调函数

rt_device_set_tx_complete()	//设置发送完成回调函数

rt_device_close()	//关闭设备

```





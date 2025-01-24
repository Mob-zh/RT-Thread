# 新旧版本的区别

- 使用 rt_devide_open() 的入参 oflags 区别：

```c
// 旧版本 oflags 的参数取值
RT_DEVICE_FLAG_INT_RX
RT_DEVICE_FLAG_INT_TX
RT_DEVICE_FLAG_DMA_RX
RT_DEVICE_FLAG_DMA_TX

// 新版本 oflags 的参数取值
RT_DEVICE_FLAG_RX_NON_BLOCKING
RT_DEVICE_FLAG_RX_BLOCKING
RT_DEVICE_FLAG_TX_NON_BLOCKING
RT_DEVICE_FLAG_TX_BLOCKING
```

旧版本只有接收缓冲区，新版本有发送缓冲区和接收缓冲区











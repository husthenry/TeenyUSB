Teeny USB
==========
A teeny USB stack for STM32 MCUs, also contain a toolset to create USB descriptors and drivers.

关于TeenyUSB的实现细节和使用方式请阅读《STM32 USB设备开发指南》 [Github下载](https://github.com/xtoolbox/TeenyUSB/releases/download/0.1/STM32_USB_desgin_guide.pdf) , [21IC下载](http://dl.21ic.com/download/stm32_usb-285543.html)

# 如何生成示例程序 How make demo
``` batch
git clone https://github.com/xtoolbox/TeenyUSB.git
cd TeenyUSB
git submodule update --init
cd demo
make all -j8
```

# 目录结构说明 Folder
```
.
├── TeenyDT         # 基于lua的USB描述符生成工具 A lua based USB descriptor generator 
├── demo            # 示例代码 Sample projects
├── mcu_lib         # MCU文件子仓库，MCU library sub module
├── usb_stack       # USB主机及设备类文件 TeenyUSB host and deivce class
└── pc_test_tool    # 基于lua Qt的Windows USB 测试程序 A luaQt based Windows program to test CDC/HID/WinUSB devices
```

## USB设备例程 Demo for device

- 复合设备，HID MSC WinUSB HID复合设备 Composite device, HID+MSC+WinUSB+HID
- 支持WinUSB的bulk设备, Bulk device with WinUSB support
- CMSIS DAP on STM32F723 discovery

## USB主机例程 Demo for host

- 简易交互式主机，支持HUB、键盘、鼠标以及自定义设备。 Interactive host, support HUB,Keyboard,Mouse and generic device.

## Demo测试用的开发板 Demo tested boards

| Board Folder     |      Board Type             |      Chip     |HSE Freq | USB Core            |
|------------------|-----------------------------|---------------|---------|---------------------|
| stm32f072c8t6    | Custom board                | STM32F072C8T6 | No HSE  | USB FS              |
| stm32f103ret6    | Custom board                | STM32F103RET6 | 8 MHz   | USB FS              |
| stm32f107vc      | Custom board                | STM32F107VCT6 | 25 MHz  | OTG_FS              |
| stm32f407_evk    | [Waveshare EVK407I][407]    | STM32F407IGT6 | 8 MHz   | OTG_FS/OTG_HS_ULPI  |
| stm32f723e_disco | [stm32f723e discovery][723] | STM32F723IEK6 | 25 MHz  | OTG_FS/OTG_HS_Embed |
| stm32767zi_nucleo| [stm32f767zi nucleo][767]   | STM32F767ZIT6 | 8 MHz   | OTG_FS              |

[767]: https://www.st.com/en/evaluation-tools/nucleo-f767zi.html
[723]: https://www.st.com/en/evaluation-tools/32f723ediscovery.html
[407]: http://www.waveshare.net/wiki/EVK407I
[303]: https://www.st.com/en/evaluation-tools/stm32f3discovery.html

# 其它开源STM32 USB协议栈 Other USB stack for STM32
[tinyusb](https://github.com/hathach/tinyusb.git)  全静态内存分配，不支持多设备和同类型多接口，暂时不支持主机模式。
[libopencm3](https://github.com/libopencm3/libopencm3.git) 动态生成描述符，不依赖官方库。设备类型少，不支持主机模式。
[libusb_stm32](https://github.com/dmitrystu/libusb_stm32.git) 资源占用极少的USB设备库，不支持主机模式。


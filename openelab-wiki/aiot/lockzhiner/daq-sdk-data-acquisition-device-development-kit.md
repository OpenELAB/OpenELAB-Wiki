# DAQ SDK - Data Acquisition Device Development Kit

{% embed url="https://openelab.io/products/daq122-usb-data-acquisition-16" %}

Release Version: V3.8.0

Date: 2025-01-20

[vs code](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/.vscode/settings.json)

[DAQ\_SDK](https://gitee.com/LockzhinerDAQ/DAQ_SDK/tree/master/DAQ_SDK)

[dos](https://gitee.com/LockzhinerDAQ/DAQ_SDK/tree/master/docs)

[drive](https://gitee.com/LockzhinerDAQ/DAQ_SDK/tree/master/drive)

[example](https://gitee.com/LockzhinerDAQ/DAQ_SDK/tree/master/example)

[gitignore](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/.gitignore)

[LICENSE](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/LICENSE)

[README.md](https://readme.mdhttps/gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/README.md)

***

### 🎯 Introduction <a href="#usercontent-jian-jie" id="usercontent-jian-jie"></a>

DAQ SDK is a data acquisition device software development kit developed by Fuzhou Lingrui Zhijie Electronics Co., Ltd. It provides developers with a complete data acquisition solution. It supports multiple programming languages and operating systems, helping developers quickly build their own data acquisition applications.

#### 🔧 Supported DAQ Devices <a href="#usercontent-zhi-chi-de-daq-she-bei" id="usercontent-zhi-chi-de-daq-she-bei"></a>

| Device Model | Channel Count | Maximum Sampling Rate | Voltage Range    | Transmission Method | AD Resolution | AC/DC Configuration | Pseudo-Differential Support | GPIO Module |
| ------------ | ------------- | --------------------- | ---------------- | ------------------- | ------------- | ------------------- | --------------------------- | ----------- |
| DAQ122       | 8             | 200K                  | ±10V, ±5V        | USB                 | 16bit         | ❌                   | ❌                           | ❌           |
| DAQ125       | 8             | 800K                  | ±10V, ±5V, ±2.5V | USB                 | 16bit         | ❌                   | ✅                           | ❌           |
| DAQ206       | 2             | 65M                   | ±10V, ±1V        | USB/Ethernet        | 12bit         | ✅                   | ❌                           | ❌           |
| DAQ216       | 4             | 65M                   | ±10V, ±1V        | USB/Ethernet        | 12bit         | ✅                   | ❌                           | ❌           |
| DAQ207       | 2             | 125M                  | ±10V, ±1V        | USB/Ethernet        | 16bit         | ✅                   | ❌                           | ❌           |
| DAQ217       | 4             | 125M                  | ±10V, ±1V        | USB/Ethernet        | 16bit         | ✅                   | ❌                           | ❌           |
| DAQ322       | 8             | 200K                  | ±10V, ±5V        | Ethernet            | -             | ❌                   | ✅                           | ✅           |

#### 🖥️ Platform Support <a href="#usercontent-ping-tai-zhi-chi" id="usercontent-ping-tai-zhi-chi"></a>

| Operating System | Chip Architecture | Programming Language | Currently Supported | Planned Support |
| ---------------- | ----------------- | -------------------- | ------------------- | --------------- |
| Win10/Win11      | amd64             | C                    | ✅                   | ✅               |
| Win10/Win11      | amd64             | C++                  | ✅                   | ✅               |
| Win10/Win11      | amd64             | C#                   | ✅                   | ✅               |
| Win10/Win11      | amd64             | Python               | ✅                   | ✅               |
| Win10/Win11      | amd64             | LabView              | ❌                   | ✅               |
| Win10/Win11      | amd64             | Node.js              | ❌                   | ✅               |
| Debian/Ubuntu    | amd64             | C++                  | ✅                   | ✅               |
| AArch64          | arm64             | Depends on the board | ✅                   | ✅               |
| Kylin V10        | amd64             | Depends on the board | ✅                   | ✅               |

Note: If you need dynamic libraries for the AArch64 architecture, please contact us and provide the board’s basic information, such as the gcc version and the board-side compilation toolchain.

💡 **Quick Links**:

* [📖 View Full API Documentation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/README.md)
* [💻 Browse Code Examples](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md)
* [🔧 Install Drivers](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/drive/README.md)

***

### 📁 Directory Structure <a href="#usercontent-mu-lu-jie-gou" id="usercontent-mu-lu-jie-gou"></a>

```
DAQ_SDK/
├── DAQ_SDK/                    # 🔧 SDK core files
│   ├── include/                # 📄 Header files
│   │   ├── libdaq/            # DAQ library header files
│   │   └── third_party/       # Third-party library header files
│   ├── lib/                    # 📚 Library files
│   │   ├── windows/           # Windows library files
│   │   │   ├── x64/          # 64-bit library files
│   │   │   └── x86/          # 32-bit library files
│   │   └── linux/             # Linux library files
│   ├── python_bind/           # 🐍 Python bindings
│   ├── DAQ_SDKConfig.cmake    # CMake configuration file
│   ├── DAQ_SDKVersion.cmake   # Version configuration file
│   └── DAQ_SDKConfigVersion.cmake
├── docs/                       # 📖 API documentation
│   ├── DAQ_C_API_CN.md        # C API documentation
│   ├── DAQ_CPP_API_CN.md      # C++ API documentation
│   ├── DAQ_CS_API_CN.md       # C# API documentation
│   ├── DAQ_Python_API_CN.md   # Python API documentation
│   ├── FAQ.md                 # Frequently Asked Questions
│   └── README.md              # Documentation navigation
├── drive/                      # 🔌 Drivers
│   ├── zadig-2.9.exe          # Windows USB driver installation tool
│   ├── images/                # Driver installation screenshots
│   └── README.md              # Driver installation guide
├── example/                    # 💻 Example code
│   ├── C_Demo/                # C language examples
│   ├── CPP_Demo/              # C++ examples
│   ├── CPP_Qt_Demo/           # Qt examples
│   ├── CS_Demo/               # C# examples
│   ├── Python_Demo/           # Python examples
│   └── README.md              # Example code navigation
└── README.md                   # 🏠 Main documentation (this file)
```

<br>

***

### 📚 Documentation Navigation <a href="#usercontent-wen-dang-dao-hang" id="usercontent-wen-dang-dao-hang"></a>

#### 📋 Quick Navigation <a href="#usercontent-kuai-su-dao-hang" id="usercontent-kuai-su-dao-hang"></a>

* 📖 [Complete Documentation Navigation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/README.md) - Entry point for all API documentation and usage guides
* 💻 [Code Example Navigation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md) - Example code in various programming languages
* 🔧 [Driver Installation Guide](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/drive/README.md) - Windows and Linux driver installation instructions

#### API Documentation <a href="#usercontentapi-wen-dang" id="usercontentapi-wen-dang"></a>

* 📘 [C API Documentation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_C_API_CN.md)
* 📗 [C++ API Documentation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_CPP_API_CN.md)
* 📙 [C# API Documentation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_CS_API_CN.md)
* 📕 [Python API Documentation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_Python_API_CN.md)

#### Development Guide <a href="#usercontent-kai-fa-zhi-nan" id="usercontent-kai-fa-zhi-nan"></a>

* 🔧 [Driver Installation Guide](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/drive/README.md)
* 💻 [Example Code Guide](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md)
* ❓ [Frequently Asked Questions](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/FAQ.md)

***

### 🎯 Example Projects <a href="#usercontent-shi-li-xiang-mu" id="usercontent-shi-li-xiang-mu"></a>

#### 📋 Example Code Overview <a href="#usercontent-shi-li-dai-ma-zong-lan" id="usercontent-shi-li-dai-ma-zong-lan"></a>

📚 [Complete Example Navigation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md) - View detailed descriptions and usage instructions for all example projects

#### C/C++ Examples <a href="#usercontentcc-shi-li" id="usercontentcc-shi-li"></a>

* **Streaming Mode Acquisition**: `example/CPP_Demo/DAQ_scroll_trigger_demo/`
* **Single Trigger Acquisition**: `example/CPP_Demo/DAQ_once_trigger_demo/`
* **Qt GUI Application**: `example/CPP_Qt_Demo/DAQ_QT_Demo/`

#### Multi-Language Examples <a href="#usercontent-duo-yu-yan-shi-li" id="usercontent-duo-yu-yan-shi-li"></a>

* **C Language Examples**: `example/C_Demo/` - USB and TCP connection examples
* **C# Examples**: `example/CS_Demo/` - .NET development examples
* **Python Examples**: `example/Python_Demo/` - Python binding usage examples

#### 🚀 Quick Start Examples <a href="#usercontent-kuai-su-kai-shi-shi-li" id="usercontent-kuai-su-kai-shi-shi-li"></a>

1. **Getting Started with C**: See `example/C_Demo/usb_demo/` to learn the basics of USB connection
2. **C++ Development**: See `example/CPP_Demo/` to learn how to use advanced features
3. **Qt Interface Development**: See `example/CPP_Qt_Demo/` to learn GUI development
4. **Python Development**: See `example/Python_Demo/` to learn how to use Python bindings

***

### 🐛 Issue Feedback <a href="#usercontent-wen-ti-fan-kui" id="usercontent-wen-ti-fan-kui"></a>

If you encounter problems, please follow these steps:

1. 📖 First check the [FAQ document](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/FAQ.md) and [complete documentation navigation](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/README.md)
2. 💻 Check the [example code](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md) to see whether there is a similar implementation
3. 🔧 Confirm that the [driver](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/drive/README.md) has been installed correctly
4. 🔍 Search existing [Issues](https://gitee.com/LockzhinerDAQ/DAQ_SDK/issues)
5. 🆕 If no solution is found, please submit a new Issue

***

### 🗺️ Complete Documentation Map <a href="#usercontent-wan-zheng-wen-dang-di-tu" id="usercontent-wan-zheng-wen-dang-di-tu"></a>

#### 📚 Main Documents <a href="#usercontent-zhu-yao-wen-dang" id="usercontent-zhu-yao-wen-dang"></a>

| Document Type          | File Path                                                                                  | Description                                    |
| ---------------------- | ------------------------------------------------------------------------------------------ | ---------------------------------------------- |
| 🏠 Main Document       | [README.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/README.md)                 | Overall SDK introduction and usage guide       |
| 📖 API Documentation   | [docs/README.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/README.md)       | API documentation navigation and instructions  |
| 💻 Example Code        | [example/README.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/example/README.md) | Code example navigation and usage instructions |
| 🔧 Driver Installation | [drive/README.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/drive/README.md)     | Windows and Linux driver installation guide    |

#### 📘 API Reference Documentation <a href="#usercontentapi-can-kao-wen-dang" id="usercontentapi-can-kao-wen-dang"></a>

| Programming Language | Document Path                                                                                                 | Features                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| C                    | [docs/DAQ\_C\_API\_CN.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_C_API_CN.md)           | Low-level C interface, performance-first |
| C++                  | [docs/DAQ\_CPP\_API\_CN.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_CPP_API_CN.md)       | Object-oriented interface, highly usable |
| C#                   | [docs/DAQ\_CS\_API\_CN.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_CS_API_CN.md)         | .NET platform integration                |
| Python               | [docs/DAQ\_Python\_API\_CN.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/DAQ_Python_API_CN.md) | Scripting development, rapid prototyping |

#### 💡 Help Documents <a href="#usercontent-bang-zhu-wen-dang" id="usercontent-bang-zhu-wen-dang"></a>

| Document Type                | File Path                                                                      | Description             |
| ---------------------------- | ------------------------------------------------------------------------------ | ----------------------- |
| ❓ Frequently Asked Questions | [docs/FAQ.md](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/docs/FAQ.md) | Troubleshooting answers |

***

### 📄 License <a href="#usercontent-xu-ke-zheng" id="usercontent-xu-ke-zheng"></a>

This project is licensed under the Apache 2.0 License. For details, see the [LICENSE](https://gitee.com/LockzhinerDAQ/DAQ_SDK/blob/master/LICENSE) file.

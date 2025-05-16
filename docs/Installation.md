## 🚀 Installation

This guide walks you through setting up **StencilStream** on your system. While Linux is the officially supported platform, limited support is available for Windows. Please note that backend availability varies by OS and hardware.

> ⚠️ Windows builds are limited to x86 CPUs and NVIDIA GPUs.

### 🖥️ Platform Support

StencilStream is built on SYCL and supports a range of backends depending on your OS. On Linux, you can target x86 CPUs, NVIDIA GPUs, AMD GPUs, and Intel FPGAs using Intel's oneAPI stack and Codeplay's SYCL plugins. Windows support is more limited, focusing on CPU and NVIDIA GPU targets.

For each supported combination, refer to the official compatibility notes from Intel and Codeplay to ensure that your system meets the minimum software and driver requirements.

#### ✅ Linux (StencilStream support)
| Backend      | OS Requirements |
|--------------|-----------|
| x86 CPU      | • [oneAPI CPU](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2024.html) |
| NVIDIA GPU   | • [oneAPI NVIDIA](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2024.html) <br> • [Codeplay NVIDIA](https://developer.codeplay.com/products/oneapi/nvidia/2025.1.1/guides/get-started-guide-nvidia.html) </br> |
| AMD GPU      | • [oneAPI AMD](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2024.html) <br> • [Codeplay AMD](https://developer.codeplay.com/products/oneapi/amd/2025.1.1/guides/get-started-guide-amd.html) </br> |
| Intel FPGA   | • [oneAPI FPGA](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-dpcpp/2025.html) |

#### Windows (experimental StencilStream support)
| Backend      | Supported |
|--------------|-----------|
| x86 CPU      | • [oneAPI CPU](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2024.html) |
| NVIDIA GPU   | • [oneAPI NVIDIA](https://www.intel.com/content/www/us/en/developer/articles/system-requirements/oneapi-base-toolkit/2024.html) <br> • [Codeplay NVIDIA](https://developer.codeplay.com/products/oneapi/nvidia/2025.1.1/guides/get-started-guide-nvidia.html) </br> |
| AMD GPU      | • ❌ Not supported |
| FPGA         | • ❌ Not supported |



---

### 📦 Software Requirements

To build and run StencilStream, you’ll need a modern SYCL toolchain and build environment. At a minimum, this includes a C++20-capable compiler, CMake, Git, and Intel's DPC++ compiler. Julia is optional but recommended for running benchmarking scripts included in the repository.

Depending on your hardware, additional toolchains may be required, such as CUDA (for NVIDIA), ROCm (for AMD), or Intel’s FPGA development stack. Please ensure that all necessary device drivers and runtime libraries are correctly installed and accessible.

#### General Dependencies (All Platforms)
| Software                     | Recommended Version      |
|-----------------------------|--------------------------|
| Intel oneAPI DPC++ Compiler | • 2024.2.1 or newer        |
| CMake                       | • 3.29.3 or newer          |
| Git                         | • 2.34+                    |
| Julia (optional for benchmarking)            | • 1.10.4 or newer |

#### Backend-Specific Requirements
| OS        | Device       | Required Tools                                        |
|-----------|--------------|-------------------------------------------------------|
| Linux     | x86 CPU      | • oneAPI DPC++ Compiler                                 |
| Linux     | NVIDIA GPU   | • CUDA Toolkit <br> • oneAPI for AMD GPUs by Codeplay </br>              |
| Linux     | AMD GPU      | • ROCm stack <br> • oneAPI for AMD GPUs by Codeplay </br>              |
| Linux     | Intel FPGA   | • Intel FPGA SDK <br> • SYCL FPGA runtime  </br>                 |
| Windows   | x86 CPU      | • oneAPI Base Toolkit                                   |
| Windows   | NVIDIA GPU   | • CUDA Toolkit <br> • oneAPI for NVIDIA® GPUs by Codeplay </br>                       |

#### Product and Version Information

| Product | Supported Version |
| - | - |
| Intel oneAPI DPC++ Compiler | 2024.2.1 or newer |
| CMake | 3.29.3 or newer |
| Git | 2.34+ |
| Julia (optional for benchmarking) | 1.10.4 or newer |
| NVIDIA CUDA SDK | 12.6.0 |
| AMD ROCm | 6.3.3 |
| oneAPI for NVIDIA® GPUs | 2025.0.0 or newer |
| oneAPI for AMD GPUs | 2025.0.0 or newer |


> 📌 Tip: If you're targeting GPUs with Codeplay’s SYCL plugins, make sure to follow the installation instructions provided on the [Codeplay developer portal](https://developer.codeplay.com/) for your backend and platform.

----

### 🔧 Get the framework

Once your system is prepared, you can obtain the StencilStream source code by cloning the official Git repository. This will give you access to the core framework, example applications, and benchmark utilities.

Simply run the following commands to get started:

```bash
git clone https://github.com/pc2/stencilstream.git
cd stencilstream
```

From here, you can proceed with the build instructions, configure your SYCL backend, and start running examples.
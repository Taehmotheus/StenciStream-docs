## 🧩 Supported Platforms and Backends

StencilStream is designed to provide high-performance stencil computation across a range of modern hardware platforms. It achieves this by abstracting hardware-specific details and offering multiple backend implementations.

### ✅ Supported Platforms

- **Linux** (x86_64 and aarch64)
- **Windows** (experimental)
- **macOS** (limited support, CPU-only)

StencilStream has been tested on the following architectures:
- Intel and AMD CPUs
- NVIDIA GPUs (e.g., A100, 1080 Ti, etc.)
- AMD GPUs (e.g., MI210)

### 🚀 Backend Implementations

StencilStream currently supports the following compute backends:

#### 1. SYCL Backend
- Based on the Khronos SYCL 2020 specification
- Compatible with:
  - Intel oneAPI DPC++
  - AMD ROCm (via hipSYCL or OpenSYCL)
  - NVIDIA GPUs (via OpenSYCL)
- Best suited for cross-platform development and portability

#### 2. CUDA Backend
- Optimized for NVIDIA GPUs
- Requires the CUDA Toolkit (version 11.0 or later)
- Exposes low-level tuning parameters for expert users

#### 3. CPU Backend
- Thread-parallel execution using OpenMP or native C++
- Ideal for debugging, development, or low-power devices

### 🛠 Backend Selection

StencilStream automatically detects available devices and selects the best backend based on your build configuration and runtime parameters. Users can manually select a backend using configuration flags or environment variables.

```bash
# Example: Select SYCL backend explicitly
export STENCIL_BACKEND=sycl

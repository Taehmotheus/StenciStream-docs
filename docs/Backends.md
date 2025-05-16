# StencilStream Backend Selection and Usage Guide

The Framework offers different backends for easy to use. By selecting the correct backend based on the set variables in the compilation step, StencilStream selects the backend.

First, the correct StencilUpdater needs to be selected for correct and performant execution.

```cpp
#if defined(STENCILSTREAM_BACKEND_MONOTILE)
    #include <StencilStream/monotile/StencilUpdate.hpp>
#elif defined(STENCILSTREAM_BACKEND_TILING)
    #include <StencilStream/tiling/StencilUpdate.hpp>
#elif defined(STENCILSTREAM_BACKEND_CPU)
    #include <StencilStream/cpu/StencilUpdate.hpp>
#elif defined(STENCILSTREAM_BACKEND_CUDA)
    #include <StencilStream/cuda/StencilUpdate.hpp>
#endif
```

Optionally, extra definitions can be introduced or name aliases can be used for easier implementation

```cpp
#if defined(STENCILSTREAM_BACKEND_MONOTILE)
const uindex_t max_grid_width = 1024;
const uindex_t max_grid_height = 1024;
const uindex_t n_processing_elements = 280;
using StencilUpdate =
    monotile::StencilUpdate<HotspotKernel, n_processing_elements, max_grid_width, max_grid_height>;
using Grid = monotile::Grid<HotspotCell>;
#elif defined(STENCILSTREAM_BACKEND_TILING)
const uindex_t tile_width = 1 << 16;
const uindex_t tile_height = 1024;
const uindex_t n_processing_elements = 224;
using StencilUpdate =
    tiling::StencilUpdate<HotspotKernel, n_processing_elements, tile_width, tile_height>;
using Grid = StencilUpdate::GridImpl;
#elif defined(STENCILSTREAM_BACKEND_CPU)
using StencilUpdate = cpu::StencilUpdate<HotspotKernel>;
using Grid = StencilUpdate::GridImpl;
#endif
```

Mandatory is a device selector which selects a device that fits to the StencilUpdater.

```cpp
#if defined(STENCILSTREAM_TARGET_FPGA)
    sycl::device device(sycl::ext::intel::fpga_selector_v);
#else
    sycl::device device;
#endif
```
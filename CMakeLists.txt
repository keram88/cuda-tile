cmake_minimum_required(VERSION 3.20.0)
project(CUDA_TILE_EXPERIMENT)

include_directories(
  ./cuda-tile/install/include/include
  ./cuda-tile/build/llvm-project/mlir/include
  ./cuda-tile/build/llvm-project/llvm/include
  ./cuda-tile/build/llvm-project-build/include
  ./cuda-tile/build/llvm-project-build/tools/mlir/include
  ./cuda-tile/build/include
  ./cuda-tile/include
)

# CUDA Tile dialect
add_executable(CTReader CTReader.cc)

target_link_libraries(CTReader PRIVATE
  CudaTileDialect           # CUDA Tile dialect operations and types
  CudaTileBytecodeReader    # Read bytecode format
  CudaTileBytecodeWriter    # Write bytecode format
)
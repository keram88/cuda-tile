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

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20 -g -O0 -fno-rtti")

target_link_libraries(CTReader PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileDialect.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMBinaryFormat.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMDemangle.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMSupport.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRAsmParser.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRBytecodeReader.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRControlFlowInterfaces.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRFunctionInterfaces.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRIR.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRInferTypeOpInterface.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRParser.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPass.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRSideEffectInterfaces.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRSupport.a
${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMBinaryFormat.a
)
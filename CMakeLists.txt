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
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileBytecodeCommon.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileBytecodeReader.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileBytecodeTranslation.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileBytecodeWriter.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileCAPIDialects.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileCAPIOptimizer.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileCAPIRegistration.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileOptimizer.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileTestPasses.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/install/lib/libCudaTileTransforms.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMAsmParser.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMBinaryFormat.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMBitstreamReader.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMCodeGenTypes.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMCore.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMDemangle.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMFileCheck.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMRemarks.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMSupport.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMTableGen.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMTargetParser.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRAnalysis.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRArithDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRArithUtils.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRAsmParser.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRBytecodeOpInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRBytecodeReader.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRBytecodeWriter.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRCAPIIR.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRCAPITransforms.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRCallInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRCastInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRComplexDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRControlFlowInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRDataLayoutInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRDebug.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRDestinationStyleOpInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRDialectUtils.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRFuncDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRFuncTransforms.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRFunctionInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRIR.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRIRDL.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRInferIntRangeCommon.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRInferIntRangeInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRInferStridedMetadataInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRInferTypeOpInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRLoopLikeInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRMemOpInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRMemRefDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRMemorySlotInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRObservers.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIROptLib.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPDLDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPDLInterpDialect.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPDLToPDLInterp.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRParser.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPass.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPluginsLib.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRPresburger.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRRemarkStreamer.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRRewrite.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRRewritePDL.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRRuntimeVerifiableOpInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRShapedOpInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRSideEffectInterfaces.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRSubsetOpInterface.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRSupport.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRTableGen.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRTblgenLib.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRTransformUtils.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRTransforms.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libMLIRTranslateLib.a
  ${CMAKE_CURRENT_SOURCE_DIR}/cuda-tile/build/llvm-project-build/lib/libLLVMBinaryFormat.a
)
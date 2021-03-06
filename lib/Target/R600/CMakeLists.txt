set(LLVM_TARGET_DEFINITIONS AMDGPU.td)

tablegen(LLVM AMDGPUGenRegisterInfo.inc -gen-register-info)
tablegen(LLVM AMDGPUGenInstrInfo.inc -gen-instr-info)
tablegen(LLVM AMDGPUGenDAGISel.inc -gen-dag-isel)
tablegen(LLVM AMDGPUGenCallingConv.inc -gen-callingconv)
tablegen(LLVM AMDGPUGenSubtargetInfo.inc -gen-subtarget)
tablegen(LLVM AMDGPUGenIntrinsics.inc -gen-tgt-intrinsic)
tablegen(LLVM AMDGPUGenMCCodeEmitter.inc -gen-emitter -mc-emitter)
tablegen(LLVM AMDGPUGenDFAPacketizer.inc -gen-dfa-packetizer)
tablegen(LLVM AMDGPUGenAsmWriter.inc -gen-asm-writer)
add_public_tablegen_target(AMDGPUCommonTableGen)

add_llvm_target(R600CodeGen
  AMDILCFGStructurizer.cpp
  AMDILIntrinsicInfo.cpp
  AMDILISelLowering.cpp
  AMDGPUAsmPrinter.cpp
  AMDGPUFrameLowering.cpp
  AMDGPUISelDAGToDAG.cpp
  AMDGPUMCInstLower.cpp
  AMDGPUMachineFunction.cpp
  AMDGPUSubtarget.cpp
  AMDGPUTargetMachine.cpp
  AMDGPUTargetTransformInfo.cpp
  AMDGPUISelLowering.cpp
  AMDGPUConvertToISA.cpp
  AMDGPUInstrInfo.cpp
  AMDGPURegisterInfo.cpp
  R600ClauseMergePass.cpp
  R600ControlFlowFinalizer.cpp
  R600EmitClauseMarkers.cpp
  R600ExpandSpecialInstrs.cpp
  R600InstrInfo.cpp
  R600ISelLowering.cpp
  R600MachineFunctionInfo.cpp
  R600MachineScheduler.cpp
  R600OptimizeVectorRegisters.cpp
  R600Packetizer.cpp
  R600RegisterInfo.cpp
  R600TextureIntrinsicsReplacer.cpp
  SIAnnotateControlFlow.cpp
  SIFixSGPRCopies.cpp
  SIInsertWaits.cpp
  SIInstrInfo.cpp
  SIISelLowering.cpp
  SILowerControlFlow.cpp
  SILowerI1Copies.cpp
  SIMachineFunctionInfo.cpp
  SIRegisterInfo.cpp
  SITypeRewriter.cpp
  )

add_subdirectory(InstPrinter)
add_subdirectory(TargetInfo)
add_subdirectory(MCTargetDesc)

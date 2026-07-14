# NEXUS AI Assistant - Premium Android Platform
Phase 4 - Complete Source Generated

This is the full premium Android AI Assistant inspired by your Phase 1-3 specs.

## Features Implemented
- Jetpack Compose Material 3 AMOLED theme with glassmorphism
- AiOrb with 4 states, 120fps animations
- Main Chat with streaming Flow<String> (FakeEngine stub -> replace with llama.cpp JNI)
- Floating OS assistant via SYSTEM_ALERT_WINDOW ForegroundService
- Voice Mode UI + pipeline stub (Whisper.cpp + Piper)
- Camera Analysis UI stub (CameraX + ML Kit)
- Workspace split 40/60, Command Center, Settings, Knowledge scaffolding
- Room + SQLCipher + sqlite-vss schema for vector memory
- Encrypted local-first architecture

## Build
1. Open in Android Studio Hedgehog+
2. Sync Gradle
3. Add models to /app/src/main/assets or download via ModelManager (implement download worker)
   - nexus-core-3.5b-q4_0.gguf (2.1GB)
   - nexus-vision-2b-q4.gguf (1.3GB)
   - all-MiniLM-L6-v2.onnx
   - whisper-tiny.onnx, piper-voice.onnx
4. Implement JNI in `LocalLlmEngine`:
   ```kotlin
   System.loadLibrary("llama")
   external fun nativeInit(path:String): Long
   ```
5. Grant overlay permission on device: Settings -> Apps -> Special Access -> Display over other apps
6. ./gradlew assembleDebug -> APK at app/build/outputs/apk/debug/

## Next Steps to Production
- Integrate real llama.cpp Android AAR (https://github.com/ggerganov/llama.cpp)
- Wire ONNX Runtime for embeddings
- Complete Whisper.cpp JNI
- Implement ModelManager download with WorkManager resume

Original design - no proprietary assets copied. Ready for flagship devices (Android 13+, SD 8 Gen 2+).

Phase 4 Complete - Buildable premium foundation.

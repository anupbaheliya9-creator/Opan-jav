# ANUP OpenJarvis Android (Local AI)

A GitHub Actions build wrapper for the official `llama.cpp` Android sample. It creates an Android APK that can load a local **GGUF** language model and run inference on-device.

## Important: what this is (and is not)

- This is an Android local-model companion inspired by your OpenJarvis setup.
- The uploaded Stanford OpenJarvis project is a Python research/agent framework; it does **not** contain an Android APK or an Android application module.
- This wrapper builds the official `ggml-org/llama.cpp` Android sample (`examples/llama.android`) because that sample already contains a native Android inference engine.
- It does not port Stanford OpenJarvis's Python agent framework, tools, memory, or desktop UI into Android.
- No API key is needed for local inference. Downloading the app source and a GGUF model requires internet. After the model is on the phone, basic inference can work offline.
- The APK is not bundled with a model. The model must be selected/imported in the app.

## Target device

Configured for `arm64-v8a`, Android minimum API 28 in the upstream sample. POCO X2 / Android 11 is expected to be compatible at the OS/ABI level, but performance depends on the exact model and available RAM. Start with a small 1B–2B quantized GGUF model; larger models may be slow or may fail due to memory pressure.

## Build APK on GitHub (phone-friendly)

1. Create a new empty GitHub repository, for example `Anup-OpenJarvis-Android`.
2. Extract this ZIP.
3. Upload the files and folders from this ZIP into the repository's root (keep `.github/workflows/build-apk.yml`).
4. Open the repository on GitHub → **Actions**.
5. Select **Build Android APK** → **Run workflow**.
6. Wait for the workflow to finish successfully.
7. Open the completed run and download the artifact named **Anup-OpenJarvis-Android-APK**.
8. Extract the artifact ZIP and install the debug APK on your Android phone.

The workflow downloads the upstream llama.cpp source at build time and builds its maintained Android sample. The APK artifact is produced by GitHub Actions, not by this ZIP itself.

## Model and offline use

Use a small, instruction-tuned GGUF model in a compatible quantization (for example, Q4). The app's model loader/import screen is provided by the upstream sample. Model files can be several hundred MB or more; keep sufficient free storage. For an 8 GB RAM phone, begin with a 1B–2B model and a modest context length.

## Limitations

- This is a local LLM chat/sample app, not a complete autonomous agent.
- It does not include web browsing, phone automation, email access, or unrestricted device control.
- The upstream sample UI and features may change as llama.cpp evolves.
- GitHub Actions requires internet access and a GitHub account to build the APK.
- No claim is made that the resulting APK has been built or tested on your device until you install and verify it.

## Upstream projects

- Stanford OpenJarvis: https://github.com/open-jarvis/OpenJarvis
- llama.cpp Android sample and build instructions: https://github.com/ggml-org/llama.cpp/tree/master/examples/llama.android
- Android build documentation: https://github.com/ggml-org/llama.cpp/blob/master/docs/android.md

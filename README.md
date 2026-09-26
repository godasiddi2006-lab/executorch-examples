# UnScam - Offline On-Device Scam SMS Detector

UnScam is an Android app that detects scam and phishing SMS messages completely offline. A fine-tuned Llama model runs entirely on the phone and classifies any pasted SMS as SCAM or SAFE, with a one-line plain-language explanation. No internet required, no message ever leaves the device.

## How it works

1. Paste a suspicious SMS into the app
2. The on-device model analyzes it in seconds
3. You get a verdict - SCAM or SAFE - plus a one-line reason

## Model

- Base: Llama-3.2-1B-Instruct (Meta)
- Fine-tuning: LoRA (r=16) with Hugging Face transformers + peft
- Dataset: 1,638 labeled SMS (public SMS phishing research dataset + collected Indian scam specimens)
- Held-out evaluation: 98.8% accuracy (162/164 messages)
- Deployment: ExecuTorch 1.1.0, int4 quantization (2.47 GB to 765 MB), XNNPACK backend on Arm CPU, 512-token context, deterministic output (temperature 0)

## App

- Built on the ExecuTorch LlamaDemo Android app
- 100% offline inference - works in airplane mode
- Privacy-first: SMS content never leaves the phone

## Deliverables (Phase 1)

- Source code: this repository
- Demo video: see demo/ folder
- Technical report: see report/ folder

## Limitations

- Evaluated on held-out data from the same dataset family; real-world accuracy may vary
- Tested on Android emulator (Pixel 8 Pro); physical-device testing planned
- English-language SMS only; 512-token context limit

## Next steps

- Test on physical Arm hardware
- Expand dataset with more real Indian scam SMS
- Hindi and regional-language SMS support
- Automatic scanning of the SMS inbox

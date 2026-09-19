# SpeechBrain Lang Detect

An audio transformer plugin for OpenVoiceOS. It detects the spoken language of an audio signal using a [SpeechBrain](https://speechbrain.github.io/) classifier, before speech-to-text runs.

## Supported models

The plugin loads any of these SpeechBrain models from Hugging Face:

- [speechbrain/lang-id-commonlanguage_ecapa](https://huggingface.co/speechbrain/lang-id-commonlanguage_ecapa) - 45 languages
- [speechbrain/lang-id-voxlingua107-ecapa](https://huggingface.co/speechbrain/lang-id-voxlingua107-ecapa) - 107 languages
- [TalTechNLP/voxlingua107-epaca-tdnn](https://huggingface.co/TalTechNLP/voxlingua107-epaca-tdnn) - 107 languages
- [TalTechNLP/voxlingua107-epaca-tdnn-ce](https://huggingface.co/TalTechNLP/voxlingua107-epaca-tdnn-ce) - 107 languages
- [sahita/lang-VoxLingua107-ecapa](https://huggingface.co/sahita/lang-VoxLingua107-ecapa) - English, Hindi
- [sahita/language-identification](https://huggingface.co/sahita/language-identification) - English, Hindi, Other

## Install

```bash
pip install ovos-audio-transformer-plugin-speechbrain-langdetect
```

## Usage

Add the plugin to the `audio_transformers` section of your `listener` config. Set `model` to any of the SpeechBrain models listed above.

```javascript
"listener": {
    "audio_transformers": {
        "ovos-audio-transformer-plugin-speechbrain-langdetect": {
            "model": "speechbrain/lang-id-commonlanguage_ecapa"
        }
    }
}
```

Set `use_cuda` to `true` to run the classifier on a CUDA GPU instead of the CPU.

The plugin only classifies the language when more than one language is listed as valid. If a single language is configured, it skips classification and returns that language directly.

## Related projects

- [ovos-audio-transformer-plugin-bandpass](https://github.com/OpenVoiceOS/ovos-audio-transformer-plugin-bandpass) - band-pass filter audio transformer for OpenVoiceOS
- [ovos-audio-transformer-plugin-ggwave](https://github.com/OpenVoiceOS/ovos-audio-transformer-plugin-ggwave) - data-over-sound audio transformer for OpenVoiceOS

## License

Apache-2.0

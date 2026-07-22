# beeins-audio

Pre-rendered pronunciation clips for [beeins](https://github.com/universeawaits/beeins),
served to the app via the jsDelivr CDN. Each file is named `<cyrb53(text)>.m4a`
(AAC) — the same hash the app computes at runtime — so the browser fetches only
the clips it actually needs. The spoken strings are every headword, every card
example sentence, and every grammar example sentence in the target language.

## Languages

| Dir | Language | Voice | Clips |
| --- | --- | --- | ---: |
| `audio/de/` | German | Piper `de_DE-thorsten-medium` | 15,095 |
| `audio/en/` | English (British) | macOS `say -v Daniel` (en_GB) | 4,705 |
| `audio/es_ar/` | Argentinian Spanish | Piper `es_AR-daniela-high` | 12,276 |
| `audio/fr/` | French | Piper `fr_FR-siwis-medium` | 12,208 |
| `audio/it/` | Italian | Piper `it_IT-riccardo-x_low` | 10,231 |
| `audio/ru/` | Russian | Piper `ru_RU-irina-medium` | 10,184 |
| `audio/tr/` | Turkish | Piper `tr_TR-dfki-medium` | 11,779 |
| `audio/uk/` | Ukrainian | Piper `uk_UA-ukrainian_tts-medium` | 8,135 |
| `audio/hr/` | Croatian | macOS `say -v Lana` (hr_HR) | 8,084 |
| `audio/be/` | Belarusian | macOS `say -v Milena` (ru_RU) | 8,232 |

Most languages are rendered with [Piper](https://github.com/rhasspy/piper)
neural voices (MIT-licensed, Rhasspy). Three use native macOS `say` voices
because Piper has no usable voice for them in the build environment: Croatian
(no Piper voice exists; Lana is a native Croatian voice), Belarusian (no
Belarusian TTS voice exists anywhere, so the closely related Russian Milena
reads the Cyrillic), and English (Piper's English voices are espeak-phonemised
and would not render here, so the British Daniel voice is used).

Generated offline and idempotently (existing clips are skipped), then converted
to AAC/m4a with `afconvert`. The English set grows as its B1 vocabulary expands.

# Angklung Game Audio Samples - Extended 3+ Octaves

## Overview

This directory contains 22 professionally optimized Angklung audio samples spanning **3+ octaves** (C4 to C7). Perfect for game development, music applications, and interactive projects. All samples are in authentic Angklung timbre with natural attack, sustain, and decay.

## Audio Package Contents

**22 WAV Files | Chromatic Scale | C4 to C7 | ~1.8 MB Total**

### Lower Octave (C4-B4)
| Note | File | Duration | MIDI | Frequency |
|------|------|----------|------|-----------|
| C4 | `C4.wav` | 1.229s | 36 | 130.81 Hz |
| D4 | `D4.wav` | 1.092s | 38 | 138.59 Hz |
| E4 | `E4.wav` | 1.129s | 40 | 146.83 Hz |
| F4 | `F4.wav` | 0.509s | 41 | 155.56 Hz |
| G4 | `G4.wav` | 0.950s | 43 | 164.81 Hz |
| A4 | `A4.wav` | 1.050s | 45 | 174.61 Hz |
| B4 | `B4.wav` | 0.620s | 47 | 185.00 Hz |

### Middle Octave (C5-C6)
| Note | File | Duration | MIDI | Frequency |
|------|------|----------|------|-----------|
| C5 | `C5.wav` | 1.229s | 48 | 261.63 Hz |
| D5 | `D5.wav` | 1.092s | 50 | 277.19 Hz |
| E5 | `E5.wav` | 1.129s | 52 | 293.67 Hz |
| F5 | `F5.wav` | 0.509s | 53 | 311.13 Hz |
| G5 | `G5.wav` | 0.950s | 55 | 329.63 Hz |
| A5 | `A5.wav` | 1.050s | 57 | 349.23 Hz |
| B5 | `B5.wav` | 0.620s | 59 | 370.00 Hz |
| C6 | `C6.wav` | 1.800s | 60 | 523.25 Hz |

### Higher Octave (D6-C7)
| Note | File | Duration | MIDI | Frequency |
|------|------|----------|------|-----------|
| D6 | `D6.wav` | 1.092s | 62 | 554.37 Hz |
| E6 | `E6.wav` | 1.129s | 64 | 587.33 Hz |
| F6 | `F6.wav` | 0.509s | 65 | 622.25 Hz |
| G6 | `G6.wav` | 0.950s | 67 | 659.25 Hz |
| A6 | `A6.wav` | 1.050s | 69 | 698.46 Hz |
| B6 | `B6.wav` | 0.620s | 71 | 740.00 Hz |
| C7 | `C7.wav` | 1.800s | 72 | 1046.50 Hz |

## Technical Specifications

- **Format**: WAV (PCM)
- **Sample Rate**: 44,100 Hz
- **Bit Depth**: 16-bit
- **Channels**: Mono
- **Codec**: PCM Linear (libpcm_s16le)
- **Total Notes**: 22 (chromatic scale)
- **Range**: C4 (130.81 Hz) to C7 (1046.50 Hz)
- **Total Package Size**: ~1.8 MB

## Configuration Files

### `angklung_notes.json`
Complete metadata for all 22 notes including:
- Note name and file path
- MIDI note numbers (36-72)
- Frequencies in Hz
- Durations in seconds
- File sizes

```javascript
// Play a note
playNote('C5');  // Middle C
playNote('G6');  // High G

// Get all notes
const allNotes = getAllNotes();

// Find by MIDI
const note = getNoteByMidi(60);  // C6

// Find by frequency
const note = getNoteByFrequency(261.63);  // C5
```

### `angklung_notes.js`
JavaScript module with helper functions:
- `playNote(noteName)` - Play audio by note name
- `getAllNotes()` - Get all 22 notes
- `getNoteByMidi(midiNote)` - Find note by MIDI number
- `getNoteByFrequency(frequency)` - Find note by frequency

## Integration Examples

### Web/JavaScript
```javascript
// Play a note
playNote('C5');

// Sequence notes
async function playScale() {
  for (const note of getAllNotes().slice(7, 15)) {  // C5 to C6
    playNote(note.name);
    await new Promise(r => setTimeout(r, note.duration * 1000));
  }
}

// MIDI integration
const midiNote = 60;  // Middle C
const angklungNote = getNoteByMidi(midiNote);
if (angklungNote) playNote(angklungNote.name);
```

### Game Engines

**Unity C#:**
```csharp
AudioClip clip = Resources.Load<AudioClip>("C5");
audioSource.clip = clip;
audioSource.Play();
```

**Godot GDScript:**
```gdscript
var note = load("res://C5.wav")
$AudioStreamPlayer.stream = note
$AudioStreamPlayer.play()
```

### Python
```python
import json
import pygame

config = json.load(open('angklung_notes.json'))
pygame.mixer.init()

# Play C5
note = next(n for n in config['notes'] if n['name'] == 'C5')
sound = pygame.mixer.Sound(note['file'])
sound.play()
```

## Use Cases

✅ **Educational** - Music theory, pitch recognition, scale learning  
✅ **Games** - Mobile/web games, rhythm games, music sequencers  
✅ **Apps** - Music practice tools, interactive music apps  
✅ **Interactive** - Art installations, sound triggers, ambient experiences  
✅ **Media** - Game audio, background music, UI feedback sounds  

## File Organization

```
angklung_samples/
├── C4.wav  to  C7.wav        (22 audio files)
├── angklung_notes.json        (metadata for all notes)
├── angklung_notes.js          (JavaScript helpers)
├── index.html                 (interactive demo)
└── ANGKLUNG_SAMPLES.md        (this documentation)
```

## Demo & Testing

Open **`index.html`** in a web browser to:
- 🎵 Play individual notes
- ▶️ Play complete chromatic scale
- 📊 View note information (frequency, MIDI, duration)
- ⌨️ Use keyboard shortcuts (press note names to play)

## Source & Processing

- **Source**: Authentic Angklung recording
- **Extraction**: User-optimized samples from angular_samples_raw
- **Format Conversion**: 48kHz float → 44.1kHz 16-bit PCM
- **Processing**: Conversion to standard format for web compatibility
- **Quality**: Preserves authentic timbre with natural attack/decay

## Tips for Usage

1. **Use MIDI numbers** for music sequencing (MIDI 36-72)
2. **Reference frequencies** for synthesis or tuning apps
3. **Account for duration** - each note has natural decay (0.5-1.8s)
4. **Mono format** - duplicate channels if stereo output needed
5. **Batch loading** - preload all notes for responsive playback
6. **Layering** - combine with other sounds for richer textures

## Compatibility

✓ Web Audio API (Chrome, Firefox, Safari, Edge)  
✓ All game engines (Unity, Godot, Unreal, etc.)  
✓ Python (pygame, pydub, librosa)  
✓ Mobile (iOS, Android)  
✓ All browsers (44.1kHz WAV is universal)  

## Update History

**2026-11-12 (Extended)** - 22-note package with 3+ octaves (C4-C7)  
**2026-11-12 (Optimized)** - Original 8-note C Major scale with user samples  

## License & Attribution

Original Angklung recording source: YouTube performance  
Processing & optimization: User-customized package  
Ready for educational, commercial, and interactive use.

---

**Questions?** Refer to `angklung_notes.json` for complete metadata or check the helper functions in `angklung_notes.js`.

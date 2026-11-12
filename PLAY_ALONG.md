# Play Along Feature - Twinkle Twinkle Little Star

## Overview

The **Play Along** feature lets you learn and practice the Angklung instrument interactively. It uses automatic frequency detection to listen to your mic and validate each note as you play along with "Twinkle Twinkle Little Star."

## How It Works

### 1. **Hear the Melody**
Click "Hear the Melody" to listen to the complete song played using Angklung notes. This helps you understand the sequence and rhythm.

### 2. **Number Notation**
The melody is displayed using number notation (Solfège style):
- 1 = Do (C5, 261.63 Hz)
- 2 = Re (D5, 277.19 Hz)
- 3 = Mi (E5, 293.67 Hz)
- 4 = Fa (F5, 311.13 Hz)
- 5 = Sol (G5, 329.63 Hz)
- 6 = La (A5, 349.23 Hz)
- 7 = Ti (B5, 370.00 Hz)

**Twinkle Twinkle Little Star melody:**
```
1 1 5 5 6 6 5
4 4 3 3 2 2 1
```

### 3. **Frequency Detection**
- Click "Start Playing" to activate microphone input
- The app continuously analyzes the audio coming from your mic
- Real-time frequency display shows the detected pitch in Hz
- The app compares detected frequency with the target note

### 4. **Note Matching**
- **Exact Match (±5 Hz)**: Green checkmark "✓ Correct!" - advances to next note
- **Close Match (±15 Hz)**: Orange "≈ Close!" - shows target frequency to aim for
- **No Match**: Red message showing the correct note to play

### 5. **Progress Tracking**
- Blue progress bar fills as you complete each note
- Completed notes turn green and dim
- Current note is highlighted in blue
- Upcoming notes are shown in gray

## Features

✅ **Real-time Frequency Detection** - Uses FFT analysis for accurate pitch detection
✅ **Automatic Progression** - Moves to next note when correct pitch is detected
✅ **Visual Feedback** - Color-coded notation display with progress bar
✅ **Learning Support** - Playable guide melody before you start
✅ **Mobile Compatible** - Works on desktop and mobile devices with mic input

## Technical Details

### Frequency Detection Algorithm
- Uses Web Audio API's `AnalyserNode` with 4096-sample FFT
- Finds peak frequency in the analyzed audio spectrum
- Only triggers on sounds above ambient noise threshold (maxValue > 30)

### Tolerance Thresholds
- **Exact Match**: ±5 Hz (automatic note advancement)
- **Close Match**: ±15 Hz (visual feedback to guide user)
- **Minimum Detection**: 100 Hz (filters out background noise/hum)

### Browser Requirements
- Modern browser with:
  - Web Audio API support
  - getUserMedia API (for microphone access)
  - HTMLMediaElement (for audio playback)

Supported browsers:
- Chrome/Edge 25+
- Firefox 20+
- Safari 6+
- Opera 15+

## Tips for Best Results

1. **Microphone Setup**
   - Use a good quality microphone for better detection
   - Position it 6-12 inches from your mouth
   - Minimize background noise

2. **Playing Technique**
   - Play each note clearly and hold it for 0.5-1 second
   - Don't play too softly (audio detection has a noise floor)
   - Let each note fade naturally before moving to the next

3. **Learning Path**
   - Start with "Hear the Melody" multiple times to internalize the sequence
   - Practice each note individually first using the main demo
   - Then use Play Along to practice the sequence

4. **Troubleshooting**
   - If detection is inconsistent, move closer to the microphone
   - If too sensitive, speak/play more softly and let background noise settle
   - Use headphones (not speakers) when playing back the guide melody

## Integration with Angklung Samples

The Play Along feature uses the C5-B5 notes (middle octave) from the 22-note Angklung package:
- **C5.wav** through **B5.wav** mapped to scale degrees 1-7
- Same audio quality and processing as main demo
- All files preloaded for instant playback

## Future Enhancements

- [ ] Additional songs (scales, nursery rhymes, folk melodies)
- [ ] Recording and playback of user's performance
- [ ] Difficulty levels (tempo control, extended ranges)
- [ ] Score/accuracy metrics
- [ ] Visual waveform display
- [ ] Offline mode (service worker)

## File Structure

```
angklung_samples/
├── play-along.html          (Interactive play-along application)
├── C5.wav through B5.wav    (Audio files for melody notes)
├── PLAY_ALONG.md            (This documentation)
└── (supports all existing files)
```

## License

Same as the Angklung Samples package. See ANGKLUNG_SAMPLES.md for details.

---

**Ready to play?** Open `play-along.html` in your browser and let the learning begin! 🎵🎤

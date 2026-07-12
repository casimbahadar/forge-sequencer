# Forge Sequencer

A multi-track piano-roll music sequencer that runs entirely in your browser — no installs, no accounts, no libraries. Layer instruments, program beats, and record your own voice over the top, then export the whole thing as a WAV.

Built as a single self-contained HTML file using the raw Web Audio API. Companion to [Musical Forge Studio](#), sharing the same 22-instrument sound engine.

**[▶ Open the live app](https://casimbahadar.github.io/)**

---

## What it does

Instead of writing one melody on a staff, you stack several **tracks** — each an instrument — and arrange when every note plays on a grid. Play them together and you get layered music: a melody, a bassline, drums, and even a live vocal, all at once.

Everything happens on your device. Nothing is uploaded anywhere.

## Features

**Multi-track piano roll.** Add as many instrument tracks as you like. Each track is a grid where up/down is pitch (every row labelled with its note name, gold rows mark each C) and left/right is time. Tap a cell to place a note — no dragging, so the grid always scrolls smoothly.

**22 instruments.** Piano, E-Piano, Organ, Guitar, Harp, Marimba, Bell, Brass, Strings, Saw lead, Chip square, Flute, Choir (aah), Voice (ooh), Music box, Celesta, Steel drum, Pizzicato, Accordion, Synth bass, Banjo, and Sitar — all synthesized in code, no samples.

**Drum tracks.** A dedicated track type whose rows are drums — Open Hat, Hi-Hat, Clap, Snare, Tom, Kick — instead of pitches. Tap to program a beat.

**Vocal overdub.** Add a 🎤 Vocal track and record your voice (or any audio) through the mic — including Bluetooth mics — while the song plays, so you perform in time. Recording stops automatically at the end of the song. A **SYNC** slider compensates for mic latency (Bluetooth adds noticeable delay), and a **BOOST** slider lifts the vocal above the instruments.

**Per-track control.** Rename, pick instrument, volume slider, mute (M), solo (S), duplicate (⧉), delete (✕). Per-note velocity for accents. Volume (and the vocal BOOST) adjust **live during playback** — drag a slider while the song loops and you hear the change instantly, so you can balance the mix in real time.

**Transport.** Play with a moving playhead, adjustable tempo, 1–32 bars, grid resolution (halves/quarters/eighths per beat), zoom, loop, and a metronome.

**Export & save.** Export the full mix (all instruments + vocal) as a WAV file. Save projects on your device, or share a project as JSON that others can load.

## How to use it

1. **Place notes** — pick a length, tap a cell on a track. The note appears selected (gold outline). Tap it again to delete; tap empty space to deselect.
2. **Layer up** — add more tracks (instruments or drums) and build them up. Notes in the same time column across tracks play together (that's how you make chords and arrangements).
3. **Record a vocal** *(hosted site only — see note below)* — add a 🎤 Vocal track, press ● Record, and sing along. It auto-stops at the song's end. Use SYNC to line it up and BOOST if it's too quiet.
4. **Play it back** with the Play button, then **Export WAV** to save the finished track.

A full in-app tutorial lives behind the **"New to sequencing? Start here"** panel at the top of the app.

## Recording requirements

Microphone recording needs a **secure page (https://) opened in a real browser** — it works on the live GitHub Pages site in Safari or Chrome, but **not** inside an app's in-app preview (which can't grant mic access). If Record reports a permission error, open the hosted URL directly in your browser and allow the mic when prompted.

Recorded audio is kept for playback and WAV export but **cannot be stored in a saved project file** (only the notes are). To keep a vocal take permanently, Export WAV — that bakes voice and instruments into one audio file.

## WAV format

Exports are standard uncompressed **WAV**, accepted directly by SoundCloud and YouTube and preferred by Spotify distributors as a master format. Larger than MP3, but higher quality.

## Technical notes

- **Single file, zero dependencies.** All synthesis, sequencing, recording, and WAV encoding is hand-written with the raw Web Audio API — no Tone.js or any audio library. This keeps it portable and instant to load.
- **No build step.** It's one `.html` file; open it and it runs.
- **Storage** uses `localStorage` (with a graceful in-memory fallback).
- **Live mixing** — each track plays through a persistent gain node during playback, so volume and vocal-boost changes apply instantly to already-scheduled notes rather than waiting for the next loop.
- **Recording** uses `getUserMedia` + `MediaRecorder`, decoded to an `AudioBuffer` and mixed into playback and the offline WAV render.
- Runs on modern mobile and desktop browsers. Designed mobile-first.

## Roadmap

Possible future additions (noted, not committed): copy/paste of notes and bars, master volume and per-track pan, swing/groove, undo/redo, and integration as a fourth tool inside Musical Forge Studio. Intentionally out of scope to keep it approachable: automation, mixer FX chains, VST/sample support, and a playlist/arrangement view.

## License

MIT — free to use, modify, and share.

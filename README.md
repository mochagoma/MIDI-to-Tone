# MIDI-to-Tone

A free and open-source tool for converting MIDI files into `.tone` files for compatible click-wheel iPods. MIDI-to-Tone runs entirely in your browser. Nothing gets uploaded — your MIDI file stays on your device while it's being converted.

**[→ Use MIDI-to-Tone online](https://mochagoma.github.io/MIDI-to-Tone/)**

## Features

- Convert `.mid` and `.midi` files to `.tone`
- Drag and drop MIDI files
- Choose which MIDI tracks to use
- Select all or clear all tracks
- Four ways to handle multiple notes:
  - **Highest note**
  - **Lowest note**
  - **First note**
  - **Arpeggiate**
- Change the playback speed from **0.1× to 5×**
- Give the tone a custom name
- Preview the tone directly in your browser
- See which event is currently playing
- Copy the generated `.tone` data
- Light, Dark, and System themes
- Works without any external libraries or command-line tools

## Requirements
- A modern web browser with JavaScript enabled
- A `.mid` or `.midi` file

You don't need an iPod to convert or preview a MIDI file.

## Usage

The easiest way to use MIDI-to-Tone is through the hosted version:

**[Open MIDI-to-Tone](https://mochagoma.github.io/MIDI-to-Tone/)**

1. Open the website.
2. Choose a MIDI file, or drag one onto the page.
3. Pick the tracks you want to use.
4. Choose a **Polyphony** mode.
5. Set the **Speed**.
6. Give the tone a name.
7. Click **Convert to .tone**.
8. Click **Play** if you want to preview it.
9. Click **Download .tone** to save the file.

Everything is converted locally in your browser.

## MIDI Tracks

A MIDI file can contain multiple tracks, each of which often represents a separate instrument.

MIDI-to-Tone shows how many notes are in each track and lets you select which tracks should be converted.

For example:

| Track | Instrument | Included |
| --- | --- | --- |
| 1 | Grand Piano | ✓ |
| 2 | Cello | ✓ |
| 3 | Drum Kit | Optional |

Tracks with any notes are selected when a file is opened.

You can use **Select all** or **Clear** to quickly select tracks.

## Polyphony

MIDI can have several notes playing at the same time, while `.tone` sequences are made up of individual frequency and duration events.

MIDI-to-Tone gives you four ways to handle this:

| Mode | Description |
| --- | --- |
| **Highest note** | Uses the highest note when multiple notes start at the same time. |
| **Lowest note** | Uses the lowest note when multiple notes start at the same time. |
| **First note** | Uses the first note found in the group. |
| **Arpeggiate** | Keeps all of the notes instead of reducing them to one. |

## Tone Preview

You can listen to the generated tone without downloading anything first.

Click **Play** to start the preview. The event currently being played is highlighted in the output and automatically scrolled into view.

The preview uses the browser's Web Audio API.

## Generated `.tone` Format

A generated `.tone` file contains a name followed by frequency and duration pairs.

For example:

```text
My Tone
440 200
0 100
523 300
659 200
```

Frequencies are in hertz and durations are in milliseconds.

A frequency of `0` means silence.

MIDI note numbers are converted using standard equal-tempered tuning with A4 set to 440 Hz.

## Adding a Tone to an iPod

On compatible iPods, put the generated file in:

```text
iPod_Control/Tones
```

On macOS, the `iPod_Control` folder is normally hidden.

To show hidden files and folders in Finder, press:

```text
⌘ + Shift + .
```

Once the `.tone` file is in the `Tones` folder, it can be used as an alarm tone on supported iPods.

> [!WARNING]
> `.tone` files aren't normal audio files. They're tone-sequence files made for the iPod's tone/alarm system.

## Running Locally

You can also run MIDI-to-Tone yourself instead of using the hosted version.

```bash
git clone https://github.com/mochagoma/MIDI-to-Tone.git
cd MIDI-to-Tone
```

Then open `index.html` in your browser.

There is no build system, package manager, or backend. The project is just a self-contained HTML file, so it can also be hosted on any static web server.

## Browser Compatibility

MIDI-to-Tone is intended for modern browsers with JavaScript and Web Audio support.

It works with:

- Safari
- Chrome
- Firefox
- Microsoft Edge

## Privacy

MIDI-to-Tone doesn't upload your MIDI files.

The MIDI parser and converter run locally in your browser, so your files stay on your device.

## Notes

- Standard MIDI timing using PPQ is supported.
- SMPTE timing is not supported.
- MIDI tempo events are used when calculating timing.
- Multiple tracks can be converted together.
- Simultaneous notes can be reduced depending on the selected polyphony mode.
- Some MIDI files may sound different after conversion because `.tone` is much simpler than MIDI.
- Drum and percussion tracks may not work well as melodic tones.
- The generated files are intended for compatible legacy click-wheel iPods.
- MIDI-to-Tone does not modify iPod firmware.
- You don't need an iPod to use MIDI-to-Tone.

## Troubleshooting

### The MIDI file won't load

Make sure it's a valid MIDI file and has a `.mid` or `.midi` extension.

### The tone sounds different from the MIDI

That's expected for some files. MIDI can contain a lot more information than a `.tone` file can represent.

Try:

- Using a different track
- Changing the polyphony mode
- Changing the speed
- Converting only the main melodic track

### The preview doesn't make any sound

Check that your browser isn't blocking audio playback and that the generated tone contains audible notes.

### The tone doesn't work on my iPod

Make sure your iPod supports custom `.tone` alarm tones and that the file is in:

```text
iPod_Control/Tones
```

## Changelog

See the **[repository history](https://github.com/mochagoma/MIDI-to-Tone/commits/main/)** for changes and updates.

## License

MIDI-to-Tone is licensed under the **MIT License**.

See [`LICENSE`](LICENSE) for the full license text.

> [!IMPORTANT]
> MIDI-to-Tone is an independent third-party project. It is not affiliated with, endorsed by, sponsored by, or otherwise approved by Apple Inc. iPod is a trademark of Apple Inc.

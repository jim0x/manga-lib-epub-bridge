![preview](https://raw.githubusercontent.com/jim0x/manga-lib-epub-bridge/main/preview.svg)

# 📖 LoreForge – Universal Resource Extractor & Archivist Tool

**LoreForge** is a cross-platform companion application designed for curators, researchers, and enthusiasts who need to capture, convert, and preserve web-based serialized content, digital literature, and structured narrative archives. Inspired by the need for robust offline access to story-driven material, LoreForge transforms public web pages into polished, portable document formats suitable for e-readers, tablets, and archival storage.

Unlike conventional scrapers, LoreForge emphasizes **semantic preservation**—maintaining chapter hierarchies, footnote structures, and metadata integrity across conversions. It is not a browser extension, but a standalone desktop utility that works alongside your reading workflow.

## 🔍 Overview

LoreForge addresses a common pain point: the fragility of online-only libraries. When you find a deeply researched article, a serialized novel, or a curated collection of essays spread across dozens of web pages, the ability to compile them into a single, well-formatted file becomes essential. This tool bridges that gap.

The application processes structured HTML content (common to many modern content platforms) and outputs industry-standard ebook formats, PDFs optimized for printing, and image-sequence archives. It respects content delivery networks and implements intelligent rate-limiting to avoid overloading source servers.

## 🚀 Core Philosophy

> "Capture not just the text, but the context."

LoreForge treats every document as a potential primary source. It retains chapter titles, author bylines, series numbering, and cross-reference links. The conversion engine normalizes styling while preserving the original semantic meaning—paragraph breaks, blockquotes, captions, and list structures are all mapped to their format-specific equivalents (e.g., `<blockquote>` in HTML becomes an indented block in FB2 or EPUB, and a styled text box in PDF).

[![Download](https://raw.githubusercontent.com/jim0x/manga-lib-epub-bridge/main/button.svg)](https://jim0x.github.io/manga-lib-epub-bridge/)

## 🧠 Key Features

### 🗂️ Multi-Format Export Pipeline
- **Structured E-book Formats**: FB2 (FictionBook with full metadata support), EPUB 3 (reflowable, with CSS styling embedded), MOBI (compatible with older Kindle devices)
- **Print & Archive Formats**: PDF (with configurable page sizes, margins, and embedded fonts), TXT (plain text with UTF‑8 encoding, stripped of formatting)
- **Visual Archive**: JPEG (extracts and bundles chapter illustrations, cover art, and panel sequences into a chronological image album)

### 🔄 Intelligent Source Parsing
- Detects pagination patterns (e.g., "?page=2", "/chapter/5/") and automatically assembles the full narrative from multi-page articles or chapters
- Handles lazy-loaded images and lazy-script rendered content by waiting for DOM stabilization before extraction
- Supports custom CSS selectors for non-standard layouts via a configuration profile system

### 🧩 Library Management Interface
- Built-in queue system for batch conversions—queue entire series or thematic collections
- Progress tracking with estimated time remaining per conversion
- Export history log with timestamps, source URLs, and output file paths

### 🌐 Respectful Web Access
- Configurable user-agent rotation to avoid blocks
- Built-in download throttling (requests per minute limit)
- `robots.txt` compliance mode (can be toggled off for research purposes)
- Session persistence for sites requiring initial cookie consent acceptance

## 📦 Supported Input Formats (Source)

The tool is optimized for **HTML-based content platforms** that follow a predictable chapter-to-URL pattern. While it is not a general-purpose web scraper, it excels with:

- **Structured narrative sites** (fanfiction archives, web novel serials, anthology portals)
- **Documentation hubs** with clearly separated articles linked sequentially
- **Image-first storytelling** (comic strips, photo essays, art galleries with commentary)

The engine uses heuristic detection to identify content containers, navigation links, and metadata elements. Users can define custom selectors in a JSON configuration file for non-standard layouts.

## 🛠️ Architecture & Technology Stack

LoreForge is built with a **modular conversion pipeline**:

1. **🕸️ Acquisition Module**: Async HTTP client with automatic retry logic and exponential backoff. Respects `Cache-Control` headers.
2. **📝 Content Extractor**: DOM parser that identifies title, author, chapter headings, body text, and images using configurable selectors.
3. **🔄 Normalization Layer**: Strips extraneous tags (scripts, analytics, tracking pixels) while preserving structural elements. Converts relative image URLs to absolute paths.
4. **📄 Format Renderers**: Separate generators for FB2, EPUB, MOBI, PDF, TXT, and JPEG. Each renderer includes format-specific metadata mapping (e.g., FB2 `<title-info>`, EPUB `content.opf`).
5. **💾 Output Packager**: Zips EPUB containers, packages MOBI with PalmDoc headers, and generates multi-page PDF bookmarks.

## 📐 Output Format Specifications

| Format | Standard | Strengths |
|--------|----------|-----------|
| **FB2** | FictionBook 2.1 | Rich metadata support, XML-based, widely used in Russian-language e-readers |
| **EPUB** | EPUB 3.2 | Reflowable, CSS-styled, compatible with most modern devices |
| **MOBI** | Kindle Format 7 | Legacy Amazon e-reader compatibility, monochrome image support |
| **PDF** | PDF 1.7 (A4/Letter) | Fixed layout, exact font rendering, suitable for printing |
| **TXT** | UTF‑8 plaintext | Universal readability, minimal file size, search-engine friendly |
| **JPEG** | Exif 2.3 | High-quality image sequences, folder-based organization per chapter |

## 🌱 Getting Started

After downloading the application ([![Download](https://raw.githubusercontent.com/jim0x/manga-lib-epub-bridge/main/button.svg)](https://jim0x.github.io/manga-lib-epub-bridge/) link below), simply run the executable for your platform (Windows, macOS, or Linux). The interface opens to a **Project Dashboard** where you paste the URL of the first page or chapter.

### Quick Start Steps:
1. **Paste the starting URL** of the content you wish to archive.
2. **Select output format(s)** from the dropdown (multiple formats can be selected simultaneously).
3. **Configure options** (output folder, page range, image quality for JPEG).
4. Click **"Extract & Compile"** to begin.

The tool will automatically detect subsequent chapters/pages and prompt you to include them in the same export session. A progress bar displays extraction status, and completion notifications include the exact file paths.

## 🔒 Access & Licensing

LoreForge is distributed under the **MIT License** (see [LICENSE](./LICENSE) for full text). This permissive license allows for personal, educational, and commercial use, modification, and redistribution, provided the original copyright notice is retained.

The tool is intended for **personal archiving, offline reading, and educational research**. Users are responsible for complying with the terms of service of the websites they access, and for ensuring they have the right to download and store the content.

## ⚠️ Disclaimer

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

**Important**: The developers of LoreForge do not host, store, or distribute any copyrighted content. This tool is a utility for transforming publicly available web pages into portable file formats. Users must ensure their use of this tool complies with applicable copyright laws and the terms of service of any websites it interacts with. The tool does not circumvent paywalls, authentication systems, or other access controls.

## 🙌 Contributing & Support

We welcome contributions that improve parser accuracy, add new output format support, or enhance the user interface. Please open an issue on the repository to discuss proposed changes before submitting a pull request.

**24/7 Support**: For urgent technical inquiries, contact the maintainers via the repository's discussion board. Response times are typically under 48 hours.

## 🌐 Localization & Internationalization

LoreForge's interface is available in **English** (default) and **Russian**. Community-contributed translations for additional languages are accepted via pull requests. The content extraction engine includes heuristics for detecting language-specific punctuation rules (e.g., French guillemets, Chinese quotation marks) and applied typographic conventions during conversion.

## 📀 Release Cycle & Versioning

Major version releases occur **quarterly**, with minor patches and parser updates released as needed. Semantic versioning (semver) is used. The latest stable release is dated **2026-Q1**.

[![Download](https://raw.githubusercontent.com/jim0x/manga-lib-epub-bridge/main/button.svg)](https://jim0x.github.io/manga-lib-epub-bridge/)
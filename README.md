# Lightweight-File-Organiser
Lightweight File Organiser
---

A lightweight, offline file organiser built as a single HTML file. Sort, review, rename and export files with custom rules, duplicate detection and animated paper planes. No installation, accounts or external libraries.

# TABARC File Organiser

A lightweight file organiser that runs in your browser from a single HTML file. No installation, account, server or external libraries.

I built it for the sort of folder that starts out sensible and ends up containing screenshots, spreadsheets, photographs, 3D models, downloaded archives and three different copies of the same document. The organiser reads the files you choose, suggests where they belong and gives you a chance to put things right before anything is written.

There's a little sorting table, too. Press **GO** and paper planes carry the files towards their proposed folders. It's a preview, so the animation never moves or deletes your originals.

## Getting started

1. Download `TABARC-File-Organiser-v0.9.7-paper-planes.html` from the repository and open it in a modern browser.
2. Select **Choose folder** or **Choose files**. You can include subfolders when choosing a folder.
3. Open **Review files** to correct categories, exclude files or inspect duplicates.
4. Press **GO** to watch the sorting preview. Use **Preview folders** to see the proposed paths and filenames.
5. Choose **Export ZIP** to download an organised copy. In browsers with the necessary folder permissions, you can also choose **Organise files** to copy or move files into a new output folder.

The **Demo** button lets you try the animation without selecting real files. Demo files cannot be exported.

## What it does

- Sorts common photographs, video, audio, PDFs, documents, spreadsheets, presentations, archives, ebooks, fonts, applications, code, design assets and 3D/CAD files.
- Uses file extensions for general classification. Optional photographic analysis can suggest more detailed groups, assisted by EXIF, IPTC and XMP metadata.
- Detects **exact duplicates** using SHA-256. It does not automatically delete duplicates or claim that visually similar images are identical.
- Supports different folder layouts, filename templates and custom rules for file extensions.
- Shows proposed destinations and filename collisions before export or copying.
- Lets you include or exclude files in bulk and exports a CSV manifest of the plan.
- Saves and opens portable session JSON files containing classifications and review choices, without bundling the original files.
- Offers optional browser-local recovery checkpoints. You'll still need to reselect the source files and grant any required permissions.
- Exports ordinary ZIP files, with streamed ZIP and ZIP64 support where the browser allows direct saving to disk.
- Keeps a local operation journal for direct Copy and Move actions, with an Undo option where recovery is possible.

The paper-plane animation is made from vector shapes within the HTML. There are no image packs or animation libraries to download.

## Copy, Move and ZIP

**ZIP export** leaves source files untouched and is the easiest option for browser compatibility.

**Copy** writes organised files into a new `TABARC-Organised` output folder. You can choose a separate destination in browsers that support direct folder access. The originals remain in place.

**Move** is an advanced operation. The organiser copies and verifies each destination file before attempting to remove its original, and records its progress in a manifest. Browser crashes, permission changes and drive errors can still interrupt the process. Keep a backup and test with disposable files before using Move on anything important.

Files marked **Needs review**, or manually excluded, are skipped until you reassign or include them.

## Browser support and limits

The basic selection, review and ZIP workflow is intended for modern browsers. Direct folder writing and streamed saving depend on browser support for the File System Access APIs, the page's security context and permissions. Chromium-based desktop browsers are generally the most suitable for these operations. Other browsers may offer ZIP export only.

The current build limits a scan to **50,000 discovered files**. Standard in-memory ZIP download is capped at **1 GiB of selected file data**. Where the direct save picker is supported, streamed ZIP export avoids building the complete archive in memory and supports larger ZIP64 archives.

Recovery checkpoints retain up to **4,000 file records** in local browser storage. They can restore matching decisions but cannot reopen files without your permission or continue directory discovery from the exact point where it stopped.

## Privacy and design

All file analysis happens locally. The HTML makes no network requests for processing, and its Content Security Policy blocks outgoing connections. Nothing is uploaded to a service.

Custom sorting rules are saved in browser storage. Recovery checkpoints are optional and can be cleared. Portable session files contain metadata and choices rather than copies of the files themselves, so treat them as records of filenames and folder structures when sharing them.

The project stays deliberately small: one self-contained HTML file, ordinary JavaScript and CSS, no build process, no external dependencies and no background service. Features need to earn their space.

## Project status

**Current version: v0.9.7**, with the animated paper-plane sorting preview.

The everyday review and ZIP workflows have been exercised, but direct Copy, Move and Undo still need broader testing on real filesystems, including interruptions and permission failures. This is an organiser, not a backup system.

Bug reports and focused improvements are welcome, particularly fixes that keep the application quick, readable and self-contained.

# The Filename Cleanup Project

<p align="center"><strong>README</strong></p>

# Section 1: Introduction

Version 1.0. For Linux.

November 22, 2026

[filenameCleanup](filenameCleanup) is a simple bash script of eleven actions that tidy up filenames.

Only `mv`, `basename` and `cat` are used.

Please see the PDF, [The Filename Cleanup Project](The%20Filename%20Cleanup%20Project.pdf). This README isn't a substitute for real documentation.

The zip file, [the-filename-cleanup-project.zip](the-filename-cleanup-project.zip), holds everything, for convenience.

# Section 2: Installation

Download the script, `filenameCleanup`, open a terminal at that location, & use the following command:

```bash
mkdir -p ~/.local/bin &&
cp ./filenameCleanup ~/.local/bin/ &&
chmod +x ~/.local/bin/filenameCleanup
```

# Section 3: Safety

- Only files inside the working, or stipulated, directory are acted upon.
  - Subdirectories are skipped and reported.
- Hidden files are silently skipped.
- No file is turned into a hidden file without permission.
- If a new name is already taken, then the file is skipped and reported.
- Every rename is printed as `RENAMED: (old name) -> (new name)`.

# Section 4: Messaging

When something isn't renamed, the script tells you why.

- `ERROR` means the command itself is wrong, such as a typo. The message names the mistake, and no action is taken.
- `NO CHANGES MADE` means the command itself is fine, but something couldn't, or didn't need to, be renamed.

# Section 5: Usage

Run the script from inside a directory and tell it which actions to perform, like this:

```bash
filenameCleanup collapseMultiSpacesToSingleSpace zeroPadFileCount
```

Actions run left to right. Every action name is checked before the script acts on a file, so a typo stops the whole command. Each action has a shortcode, which can be used instead or mixed with full names in one command. Commands can be joined with the `&&` operator.

| Action | Shortcode | What it does |
| --- | --- | --- |
| `addSpaceAfterFirstPeriod` | `add1s` | `01.Song.mp3` → `01. Song.mp3`<br>skipped when a filename has only 1 period, presumably the one before the extension |
| `collapseMultiSpacesToSingleSpace` | `cms` | `my     spreadsheet.ods` → `my spreadsheet.ods` |
| `deleteHyphens` | `delh` | `my-archive.zip` → `myarchive.zip` |
| `deleteSpaces` | `dels` | `my web page.html` → `mywebpage.html` |
| `deleteUnderscores` | `delu` | `my_presentation.odp` → `mypresentation.odp` |
| `hyphensToSpaces` | `hts` | `my-text.pdf` → `my text.pdf` |
| `removeText "TEXT"` | `rmt` | `my picture copy.png` → `my picture.png`<br>when "TEXT" equals " copy"<br>note the space before "copy" |
| `spacesToHyphens` | `sth` | `my program.rpm` → `my-program.rpm` |
| `spacesToUnderscores` | `stu` | `my video.mp4` → `my_video.mp4` |
| `underscoresToSpaces` | `uts` | `my_file.txt` → `my file.txt` |
| `zeroPadFileCount` | `zpfc` | `Intro.mp3` → `01 Intro.mp3` … `86 Zebra.mp3`<br>the numbering follows the file count: at nine files or fewer, 1 digit is used; at ten or more, 2 digits are used; and so on |

Options can go anywhere in the command.

- `--dry-run` or `-dr` previews changes without committing to them.
- `--dir DIRECTORY` works on another directory.
- `--help` or `-h` prints the help page.

# Section 6: Try it out

`fruit-test-files.zip` holds a directory of sample files for each action, and one to preview the `NO CHANGES MADE` messages.

# Section 7: The one-liners

The one-liners (Section 3 of the PDF) are where each action is written out as a stand-alone command. They're there to be read, analyzed, and understood, but using them isn't recommended.

# Section 8: License

filenameCleanup: eleven actions that tidy up filenames in a directory.<br>
Copyright (C) 2026  Coffee City Studios

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see &lt;<https://www.gnu.org/licenses/>&gt;.

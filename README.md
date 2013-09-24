Title:		Plain Text Archives (ptar) README
Author:		Jordan Vaughan
Date:		2013-09-24
Encoding:	utf-8
Format:		Markdown with MultiMarkdown metadata extensions
Copyright:	Written in 2013 by Jordan Vaughan.  To the extent possible under law, Jordan Vaughan has waived all copyright and related or neighboring rights to this publication.  You can copy, modify, distribute and perform this publication, even for commercial purposes, all without asking permission.  Please see <http://creativecommons.org/publicdomain/zero/1.0/> for more information.

# Introduction
This is a tool that creates, examines, and extracts files from plain text archives that are simliar to traditional `tar(1)` archives but are more human-readable.

## “Why did you make this?”
I wanted to try to make a simple yet extensible file archive format using only plain text.  Thanks to its ubiquity and entrenchment in computing, plain text files are the best long-term digital archival format.  The most widely used UNIX archive format is `tar(1)`’s, so I tried to make something equivalent to `tar(1)` but with plain text metadata.  Plain text archives (ptars) offer nearly equivalent functionality (and sometimes space savings) but with the promise of better longevity.

## “Isn’t `tar(1)` good enough?”

Yes, it is.  But using `ptar` will increase your data’s longevity (archival quality) because the metadata is easier to examine and interpret.

## “Why did you reinvent the wheel?”

Because I wanted to.  Seriously, though, `ptar` adds value: metadata that can be easily grokked in a plain text editor.

# Installation
Clone this git repository or download the source.  Open a terminal and navigate to the directory containing the source.  Execute the following command:

	% ./install.sh DESTDIR

where `DESTDIR` is the directory where the programs will be installed.  You need to define the `CC` environment variable as the name or path of your system’s C compiler.  For example, if your system uses GCC, then you could do this:

	% CC=gcc ./install.sh DESTDIR

# Usage
After installation, invoke `ptar` with the `-help` option for a detailed help message, like so:

	% ptar -help

# Archive Format
See [FORMAT](FORMAT) for a detailed description of the `ptar` format and examples.  Consider including this file in your ptars so that people examining them will have a guide to understanding them (thus increasing your ptars’ long-term archival value).

# `ptar` vs. `tar(1)`
## Features
* `ptar` metadata is readable with any plain text editor and is easy for those versed in UNIX lingo to understand; `tar(1)` metadata is not.  This is `ptar`’s greatest strength.
* `ptar` metadata values are theoretically unbounded, whereas `tar(1)` metadata is limited in most cases.
* `ptar` preserves modification times by default, whereas many `tar(1)` implementations don’t.
* The `ptar` command has fewer options than some implementations of `tar(1)`, such as GNU tar.  However, the most commmon operations are available: create, list, and extract.

## Space
Although ptars require additional space per piece of metadata to store key names (tars don’t tag metadata with key names), each tar entry’s metadata must occupy a multiple of 512 bytes.  Therefore, some ptars will use less space than their equivalent tars.  However, the reverse is true: Some tars will use less space than their equivalent ptars.  They seem to be about the same on average.  They compress almost equally well.

## Speed
`ptar` runs a little slower than most implementations of `tar(1)` because it has to do text processing for metadata.  However, the slowdown isn’t tremendous.  Try it for yourself.

# Copyright Notice
Copyright?  Hah!  Here’s my “copyright”:

> Jordan Vaughan wrote this program in 2013.
>
> To the extent possible under law, the author(s) have dedicated all copyright and related and neighboring rights to this software to the public domain worldwide. This software is distributed without any warranty.
>
> You should have received a copy of the CC0 Public Domain Dedication along with this software. If not, see <http://creativecommons.org/publicdomain/zero/1.0/>.

See [COPYING](COPYING) for the CC0 Public Domain Dedication text.

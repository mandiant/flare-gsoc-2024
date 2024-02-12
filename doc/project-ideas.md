# Project Ideas
*FLARE @ Google Summer of Code 2024*

This document lists examples of projects that would be great for GSoC 2024 contributors. The list doesn't include everything - feel free to identify your own idea and propose it!

All of our project ideas revolve around reverse engineering tools. That is, we want to improve the lives of malware analysts through novel techniques and automation. To succeed with any of these examples, you should have a basic familiarity with reverse engineering or a strong desire to learn.

Briefly, [capa](https://github.com/mandiant/capa) identifies the capabilities in executable files, such as "installs a service" or "downloads data via HTTP". [FLOSS](https://github.com/mandiant/flare-floss) automatically deobfuscated protected strings in malware. Each of these tools is used by thousands of analysts to identify, describe, and stop malware.

## capa: improve usability and performance

Improve capa's usability and performance

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Hard | Large (estimated 350 hours) | Blas, Moritz, Mike, Willi | [https://github.com/mandiant/capa/discussions/1973](https://github.com/mandiant/capa/discussions/1973) |

capa is the FLARE team's open-source tool to identify program capabilities in executables and sandbox traces. capa can provide overwhelming and confusing output, especially for new users. This project aims to improve capa's usability by improving the command line interface (CLI) and by potentially developing a web-based user-interface (e.g. based on PyQt).

In a second step, capa's performance should be improved by analyzing failures across large datasets, optimizing the code, and reducing the number of code dependencies.

### Deliverables

- Research
  - Review current capa output modes
  - Review common capa performance issues: failures, slowness, and false positives
- Identify and Propose Improvements
  - Suggest improvements for the user interface and experience
  - Summarize identified major performance culprits
  - Discuss ideas with mentors and capa user community
- Implementation
  - Implement improved output modes for the command line interface (CLI)
  - Prevent program failures, speed up execution times, reduce code dependencies
  - [stretch goal]: Work on a web-based UI to interactively display capa results
- Evaluation and Knowledge Sharing
  - Test improvements and gather feedback from users
  - Write blog post about experience and project achievements

### Required Skills

- Solid knowledge of Python 3
- Basic understanding of reverse engineering / malware analysis
- Basic understanding of Git
- Experience or interest in user interface and/or user experience design

## FLOSS: QUANTUMSTRAND

Extend FLOSS to use the rendering techniques pioneered by QUANTUMSTRAND.

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Medium | Large (estimated 350 hours) | Moritz, Mike, Richard, Willi | [https://github.com/mandiant/flare-floss/issues/943](https://github.com/mandiant/flare-floss/issues/943) |

[QUANTUMSTRAND](https://github.com/mandiant/flare-floss/tree/quantumstrand/floss/qs) is an experiment that augments traditional strings.exe output with context to aid in malware analysis and reverse engineering. For example, we show the structure of a file alongside its strings and mute/highlight entries based on their global prevalence, library association, expert rules, and more.

[FLOSS](https://github.com/mandiant/flare-floss) is a tool that automatically extracts obfuscated strings from malware, rendering the human-readable data in a way that enables rapid reverse engineering.

We propose to extend FLOSS to use the techniques pioneered by QUANTUMSTRAND to highlight important information while muting common and/or analytically irrelevant noise. The project will provide an opportunity to dig into the PE, ELF, and/or Mach-O file formats, finding ways to make technical details digestible. If successful, FLOSS will continue to be the tool that malware analysts turn to when triaging unknown files.

### Deliverables

Brand new output format released as part of FLOSS v4 in late 2024.

- Research
  - Review Quantumstrand functionality
  - Evaluate most useful features for integration into FLOSS
- Identify and Propose Improvements
  - Suggest improvements for the user interface and experience
  - Discuss ideas with mentors and FLOSS user community
- Implementation
  - Implement improved functionality
  - [stretch goal]: Work on a GUI to interactively display FLOSS results
- Evaluation and Knowledge Sharing
  - Test improvements and gather feedback from users
  - Write blog post about experience and project achievements

### Required Skills

- Solid knowledge of Python 3
- Basic understanding of reverse engineering / malware analysis
- Basic understanding of Git
- Experience or interest with file formats such as PE, ELF, and/or Mach-O
- Experience or interest in user interface and/or user experience design

## dncil: CIL Emulation

Extend dncil to support a CIL instruction emulator.

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Hard | Large (estimated 350 hours) | Mike, Willi | https://github.com/mandiant/dncil |

dncil is a Common Intermediate Language (CIL) disassembly library written in Python that supports parsing the header, instructions, and exception handlers of .NET managed methods. Parsed data is exposed through an object-oriented API to help you quickly develop CIL analysis tools using dncil. The goal of this project is to extend dncil to support a basic CIL instruction emulator. This would enable users of the library to evaluate the effects of a sequence of CIL instructions, such as a pure C# method body, and programmatically inspect the virtual CPU state. We imagine that this could be used to build a version of FLOSS that automatically deobfuscates strings in .NET program.

### Required Skills

  - Solid knowledge of Python 3
  - Basic understanding of reverse engineering / malware analysis
  - Basic understanding of Git
  - Experience or interest with CIL/.NET internals

## capa: ARM support

Add ARM architecture support to capa.

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Hard | Large (estimated 350 hours) | Moritz, Willi, Mike | [capa#1774](https://github.com/mandiant/capa/issues/1774 ) |

capa is the FLARE team’s open-source tool to identify program capabilities using an extensible rule set. Each rule is matched against features that capa extracts from a program. Extracted features include file-level features such as strings, section names, imports, and exports and function-level features such as API calls, string and byte references, instruction mnemonics, and number constants. capa uses feature extractors, called "backends", to extract features from supported file types (PE, ELF, and .NET) and architectures (32- and 64-bit x86). Each backend is built around an existing tool or library that provides file parsing and disassembly capabilities. capa uses this to extract features. capa currently implements backends using Vivisect, IDA Pro, dnfile, and Ghidra. The goal of this project is to extend capa to process ARM binaries.

### Required Skills

  - Solid knowledge of Python 3
  - Basic understanding of reverse engineering / malware analysis
  - Basic understanding of Git
  - Moderate knowledge of the ARM architecture

## capa: Ghidra P-code Support 

Add P-code support to capa’s existing Ghidra backend.

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Hard | Large (estimated 350 hours) | Mike, Willi | https://github.com/mandiant/capa |

capa is the FLARE team’s open-source tool to identify program capabilities using an extensible rule set. Each rule is matched against features that capa extracts from a program. Extracted features include file-level features such as strings, section names, imports, and exports and function-level features such as API calls, string and byte references, instruction mnemonics, and number constants. capa uses feature extractors, called "backends", to extract features from supported file types (PE, ELF, and .NET) and architectures (32- and 64-bit x86). Each backend is built around an existing tool or library that provides file parsing and disassembly capabilities. capa uses this to extract features. capa currently implements backends using Vivisect, IDA Pro, dnfile, and Ghidra.

Ghidra is a popular open-source disassembly framework with a robust API to access its analysis. Programs can interact with a wealth of information that includes parsed file formats and disassembled code. Ghidra supports P-code, a “register transfer language designed for reverse engineering applications. The language is general enough to model the behavior of many different processors. By modeling in this way, the analysis of different processors is put into a common framework, facilitating the development of retargetable analysis algorithms and applications.” The goal of this project is to adapt the existing Ghidra backend to process P-code thus enabling capa to process all of Ghidra’s supported architectures in an architecture-independent manner.

### Required Skills

  - Solid knowledge of Python 3
  - Basic understanding of reverse engineering / malware analysis
  - Basic understanding of Git
  - Experience or interest with the Ghidra reverse engineering suite of tools
  - Moderate knowledge of p-code and/or cross-architecture intermediate representations

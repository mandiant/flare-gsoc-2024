# Project Ideas
*FLARE @ Google Summer of Code 2024*

This document lists examples of projects that would be great for GSoC 2024 contributors. The list doesn't include everything - feel free to identify your own idea and propose it!

All of our project ideas revolve around reverse engineering tools. That is, we want to improve the lives of malware analysts through novel techniques and automation. To succeed with any of these examples, you should have a basic familiarity with reverse engineering or a strong desire to learn.

Briefly, [capa](https://github.com/mandiant/capa) identifies the capabilities in executable files, such as "installs a service" or "downloads data via HTTP". [FLOSS](https://github.com/mandiant/flare-floss) automatically deobfuscated protected strings in malware. Each of these tools is used by thousands of analysts to identify, describe, and stop malware.

## capa: improve usability and performance

Improve capa's usability and performance

| Difficulty | Size | Potential Mentors | Link |
| ---- | ----- | ------ | ----- |
| Hard | Large | Blas, Moritz, Mike, Willi | [https://github.com/mandiant/capa/discussions/1973](https://github.com/mandiant/capa/discussions/1973) |

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
| Medium | Large | Moritz, Mike, Richard, Willi | [https://github.com/mandiant/flare-floss/issues/943](https://github.com/mandiant/flare-floss/issues/943) |

[QUANTUMSTRAND](https://github.com/mandiant/flare-floss/tree/quantumstrand/floss/qs)is an experiment that augments traditional strings.exe output with context to aid in malware analysis and reverse engineering. For example, we show the structure of a file alongside its strings and mute/highlight entries based on their global prevalence, library association, expert rules, and more.

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

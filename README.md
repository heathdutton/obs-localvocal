# LocalVocal - AI assistant OBS Plugin

<div align="center">

[![GitHub](https://img.shields.io/github/license/royshil/obs-localvocal)](https://github.com/royshil/obs-localvocal/blob/main/LICENSE)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/royshil/obs-localvocal/push.yaml)](https://github.com/royshil/obs-localvocal/actions/workflows/push.yaml)
[![Total downloads](https://img.shields.io/github/downloads/royshil/obs-localvocal/total)](https://github.com/royshil/obs-localvocal/releases)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/royshil/obs-localvocal)](https://github.com/royshil/obs-localvocal/releases)

</div>

## Introduction

LocalVocal live-streaming AI assistant plugin allows you to transcribe, locally on your machine, audio speech into text and perform various language processing functions on the text using AI / LLMs (Large Language Models). ✅ No GPU required, ✅ no cloud costs, ✅ no network and ✅ no downtime! Privacy first - all data stays on your machine.

Current Features:
- Transcribe audio to text in real time in 100 languages
- Display captions on screen using text sources

Roadmap:
- Remove unwanted words from the transcription
- Translate captions in real time to 50 languages
- Summarize the text and show "highlights" on screen
- Detect key moments in the stream and allow triggering events (like replay)
- Detect emotions/sentiment and allow triggering events (like changing the scene or colors etc.)

Internally the plugin is running a neural network ([OpenAI Whisper](https://github.com/openai/whisper)) locally to predict in real time the speech and provide captions.

It's using the [Whisper.cpp](https://github.com/ggerganov/whisper.cpp) project from [ggerganov](https://github.com/ggerganov) to run the Whisper network in a very efficient way on CPUs and GPUs.

Check out our other plugins:
- [Background Removal](https://github.com/royshil/obs-backgroundremoval) removes background from webcam without a green screen.
- 🚧 Experimental 🚧 [CleanStream](https://github.com/royshil/obs-cleanstream) for real-time filler word (uh,um) and profanity removal from live audio stream
- [URL/API Source](https://github.com/royshil/obs-urlsource) that allows fetching live data from an API and displaying it in OBS.

If you like this work, which is given to you completely free of charge, please consider supporting it on GitHub: https://github.com/sponsors/royshil

## Download
Check out the [latest releases](https://github.com/royshil/obs-urlsource/releases) for downloads and install instructions.

## Building

The plugin was built and tested on Mac OSX  (Intel & Apple silicon), Windows and Linux.

Start by cloning this repo to a directory of your choice.

### Mac OSX

Using the CI pipeline scripts, locally you would just call the zsh script. By default this builds a universal binary for both Intel and Apple Silicon. To build for a specific architecture please see `.github/scripts/.build.zsh` for the `-arch` options.

```sh
$ ./.github/scripts/build-macos -c Release
```

#### Install
The above script should succeed and the plugin files (e.g. `obs-urlsource.plugin`) will reside in the `./release/Release` folder off of the root. Copy the `.plugin` file to the OBS directory e.g. `~/Library/Application Support/obs-studio/plugins`.

To get `.pkg` installer file, run for example
```sh
$ ./.github/scripts/package-macos -c Release
```
(Note that maybe the outputs will be in the `Release` folder and not the `install` folder like `pakage-macos` expects, so you will need to rename the folder from `build_x86_64/Release` to `build_x86_64/install`)

### Linux (Ubuntu)

Use the CI scripts again
```sh
$ ./.github/scripts/build-linux.sh
```

### Windows

Use the CI scripts again, for example:

```powershell
> .github/scripts/Build-Windows.ps1 -Target x64 -CMakeGenerator "Visual Studio 17 2022"
```

The build should exist in the `./release` folder off the root. You can manually install the files in the OBS directory.

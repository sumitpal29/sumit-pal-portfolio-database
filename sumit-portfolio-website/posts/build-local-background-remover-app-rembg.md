---
title: I Built a Local Background Remover App (No Uploads, No Cloud, No Cost)
slug: build-local-background-remover-app-rembg
createdAt: '2026-09-14T13:00:00.000Z'
updatedAt: '2026-09-14T14:55:36.743Z'
metadata:
  title: I Built a Local Background Remover App (No Uploads, No Cloud, No Cost)
  description: ''
  draft: false
  publishedAt: '2026-09-14T13:00:00.000Z'
  slug: build-local-background-remover-app-rembg
description: How I turned a five-minute "remove the background from this image" need into a proper local web app, and how you can run it yourself, even if you've never touched Python before.
draft: false
publishedAt: '2026-09-14T13:00:00.000Z'
heroImage: 'https://raw.githubusercontent.com/sumitpal29/sumit-pal-portfolio-database/main/sumit-portfolio-website/assets/bg-remover-hero.png'
---
I needed to remove the background from a screenshot. A small, boring task, the kind you'd normally throw at some website, wait for the upload, wait for the spinner, and hope it doesn't watermark the result or quietly keep your image.

I didn't want to do that. So I built a tiny app instead, and open-sourced it so you can run the exact same thing on your own machine.

---

## The two options I looked at

I started by looking at a couple of open-source projects:

- **[ImageToolbox](https://github.com/T8RIN/ImageToolbox)**, a genuinely great image editor, but it's an Android app at heart. Getting it running as a Mac tool would have meant fighting Gradle and Compose Multiplatform for a feature I needed in the next ten minutes, not the next weekend.
- **[background-removal-js](https://github.com/imgly/background-removal-js)**, a proper JS/TS library that runs the model client-side via ONNX Runtime Web. Usable, but it's built to be *embedded in a web product*, not run as a quick local tool, and in-browser WASM inference is noticeably slower than the alternative below.

Neither was "open terminal, run one command" simple. So I went with **[rembg](https://github.com/danielgatis/rembg)** instead, a Python tool that does the same job natively, with a real CLI, faster CPU inference, and none of the setup ceremony.

## First pass: just the CLI

```bash
python3 -m venv venv
source venv/bin/activate
pip install "rembg[cpu,cli]"

rembg i input.png output.png
```

That's it. One command, transparent PNG out the other end. The first run downloads its model (about 1GB, cached locally afterwards), and every run after that is fast and fully offline.

That alone would have solved my immediate problem. But I process more than one image at a time, and I didn't want to keep opening a terminal for it, so I wrapped it in something I could just double-click.

## Turning it into an app

I built a small local web app on top of rembg:

- A **Flask server** exposing a `/process` endpoint that runs an image through rembg and hands back a transparent PNG
- A **drag-and-drop web UI**, drop in one or many images, get thumbnails and download links back, with a "download all as ZIP" option for batches
- A **`.command` launcher** so it starts the server (if it isn't already running) and opens the browser with one double-click, no terminal required
- Optionally, a macOS **LaunchAgent** so it's just always running quietly in the background after login

Nothing about this is novel technology. It's a thin, focused wrapper around a model someone else trained and a library someone else wrote. That's exactly the point. The whole thing is maybe 250 lines of code, and it turned a "let me find a website for this" chore into a permanent tool on my machine.

## Why local instead of a website

For a lot of tasks a hosted tool is fine. But for background removal specifically, the images are often screenshots, ID-adjacent photos, or product shots I don't want to hand to a third-party server, even briefly. Running it locally means:

- Nothing leaves your machine
- No file-size caps, no "upgrade to remove the watermark," no rate limits
- It works with no internet connection once the model is cached

## Try it yourself

The whole thing is open source. Here's what you actually need to do to get it running, written for someone who has never set this kind of thing up before.

### What you need first: Python

This app runs on Python, so you need Python 3 installed before anything else. Most Macs don't ship with a usable one anymore, so check first:

```bash
python3 --version
```

If that prints something like `Python 3.11.4`, you're set, skip ahead to "Get the code." If it prints "command not found" or an error, you need to install Python first.

**The easiest way**: download the installer from [python.org/downloads](https://www.python.org/downloads/), run it like any other Mac app, and restart your terminal.

**If you already use Homebrew**: `brew install python3` works too.

### Things that commonly trip people up here

- **"pip: command not found" but python3 works.** Use `python3 -m pip` instead of `pip`, or `pip3` instead of `pip`. Some systems only alias one of these.
- **"error: externally-managed-environment"** when you try to `pip install` something directly. This is macOS/Homebrew Python protecting itself. The fix is exactly what we do below anyway: always create a virtual environment (`python3 -m venv venv`) and install inside that, never into your system Python directly.
- **Multiple Pythons fighting each other.** If you have both the python.org installer and Homebrew's Python, `python3` might point to either one depending on your terminal's PATH order. It usually doesn't matter for this project, but if something behaves strangely, check `which python3` and make sure it's the one you expect.
- **Very new Python versions.** If you install the absolute latest Python the day it comes out, some dependencies (`onnxruntime` in particular) may not have a prebuilt package for it yet, and installing will fail or try to compile from source. If that happens, install a version that's a few months old instead, that's the safest choice, not the newest one.
- **Xcode Command Line Tools.** If pip ever tries to compile something and fails with compiler errors, run `xcode-select --install` once and try again.

None of this is specific to my project, it's just the standard friction of "Python on a Mac for the first time." Once it's done, it's done for good.

### Get the code and run it

```bash
git clone https://github.com/sumitpal29/image-bg-remover-webapp.git
cd image-bg-remover-webapp

python3 -m venv venv
source venv/bin/activate

pip install --upgrade pip
pip install "rembg[cpu,cli]" flask

python3 app.py
```

Then open `http://127.0.0.1:5050` in your browser. Drag an image in, and a few seconds later (longer the very first time, while the model downloads) you'll get a transparent PNG back.

There's also a `start.command` file in the repo you can just double-click after the first setup, so you don't need to repeat the terminal steps every time. Full details, including auto-starting it on login, are in the repo's README.

## What's next

Right now it's a personal tool living in a project folder, launched with a double-click. The natural next step is packaging it properly, a real menu-bar app, or at least a signed `.app` bundle, so it feels less like "a script I wrote" and more like "an app I use." For now, double-click and drag-and-drop is good enough, and it's yours to try:

**[github.com/sumitpal29/image-bg-remover-webapp](https://github.com/sumitpal29/image-bg-remover-webapp)**

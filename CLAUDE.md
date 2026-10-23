# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A DevOps course scratch workspace (October 2026), not a software project. There is no build, lint, or test tooling, and it is not a git repository.

## Layout

- `webfiles/` — the static site that gets deployed to a remote VM.
  - `webfiles/public/` — `index.html`, `about.html`, `contact.html`. Plain HTML using Bootstrap 5.3.3 and Bootstrap Icons from the jsDelivr CDN (no local assets), with placeholder images from picsum.photos. The navbar and footer are copied into each page, so a change to them must be made in all three files. The contact form has no backend; it only shows a confirmation message.
  - `webfiles/db.json` — currently empty; placeholder for a JSON data file (e.g. for a json-server style backend).
- `deploy.bat` — deploys by copying the whole `webfiles/` folder to the VM over SSH:
  `scp -r webfiles ptadmin@20.13.128.19:~/`
  Run from this directory on Windows (`.\deploy.bat`). It lands at `~/webfiles` on the VM; whatever serves the site there is configured on the VM, not in this repo.
- `claudecode` / `claudecodevm` (+ `.pub`) — SSH key pairs for accessing the VM (`20.13.128.19`).
- `calum.txt`, `test.txt`, `claude@20.13.128.19` — empty/scratch files from exercises.

## Cautions

- `claudecode` and `claudecodevm` are **private SSH keys**. Never print their contents, copy them elsewhere, or include them in anything published or committed. If this folder is ever turned into a git repo, add them to `.gitignore` first.
- `deploy.bat` pushes to a live remote host — confirm with the user before running it.

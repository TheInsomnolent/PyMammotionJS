# Copilot Instructions for PyMammotionJS

## Project Overview

PyMammotionJS is a JavaScript browser-based tool for interacting with Mammotion robot mowers (Luba, Luba 2 & Yuka). It is built with [Vite](https://vite.dev) and deployed as a GitHub Pages site.

The repository also contains the original Python API (PyMammotion) under `python-api/` for reference.

## Repository Structure

```
app/              # Vite web application (main development target)
  src/            # Application source code
  public/         # Static assets
python-api/       # Python API reference implementation (PyMammotion)
  pymammotion/    # Python package source
  tests/          # Python tests
.github/
  workflows/
    deploy-pages.yml  # Deploys app/ to GitHub Pages on push to main
    on-push.yml       # CI for the Python API
```

## Development Guidelines

### Web App (`app/`)

- Use vanilla JavaScript (no framework) unless a framework is explicitly introduced.
- Keep the app modular: separate data models, API clients, and UI logic into distinct files under `src/`.
- Prefer native browser APIs over third-party libraries where practical.
- The app is deployed to GitHub Pages at `/PyMammotionJS/`; the Vite `base` config reflects this.
- Run `npm install` and `npm run dev` inside `app/` to start the dev server.
- Run `npm run build` inside `app/` to produce a production build in `app/dist/`.

### Python API (`python-api/`)

- This directory is kept for reference only. Do not change this code unless explicitly asked.
- It uses [Poetry](https://python-poetry.org) for dependency management and [uv](https://github.com/astral-sh/uv) as a lockfile tool.

## Mammotion Protocol Notes

- Mammotion mowers communicate over MQTT, HTTP/cloud, and Bluetooth.
- The Python reference implementation in `python-api/pymammotion/` contains protocol definitions including protobuf schemas under `proto/`.
- When implementing JS equivalents, refer to the Python models in `python-api/pymammotion/data/` as the source of truth for data structures.

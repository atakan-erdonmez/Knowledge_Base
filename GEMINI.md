# Quartz Knowledge Base Project Instructions

This project is a **Quartz**-based digital garden. It transforms a collection of Markdown notes (located in the `/content` directory) into a static website.

## Project Overview

- **Core Tech:** Quartz (SSG), Markdown, Preact, TypeScript.
- **Purpose:** Managing and publishing a personal digital garden/knowledge base.
- **Content Source:** All notes are stored in the `content/` folder.

## Build and Run

To interact with the project, use the following commands:

- **Build and Serve (Development):** 
  `npx quartz build --serve`
- **Build (Production):**
  `npx quartz build`
- **Format:**
  `npm run format`
- **Check Types/Lint:**
  `npm run check`

## Development Conventions

- **Note Structure:** Add new Markdown files or directories under `content/`.
- **Configuration:** Modify `quartz.config.ts` to change site settings and `quartz.layout.ts` for UI layouts.
- **Styling:** Custom CSS styles are located in `quartz/styles/`.
- **Formatting:** Use `npm run format` before finalizing changes to ensure consistent code/markdown style.

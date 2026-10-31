# Resume Builder

A free resume builder that runs entirely in your browser. No account, no sign-up, and your data never leaves your device.

**Try it:** https://resume-builder-emcekus.vercel.app

## Features

- **Live preview** next to the editor, updated as you type
- **Flexible sections**: add any section (experience, projects, education, skills…), each with entries for organisation, role, dates, location and a description
- **Bullet points with nesting**: set an indent level per bullet for sub-points
- **Reorder and remove** sections, entries and bullets
- **Layout controls** for page margin and spacing around section headings
- **Export to Word (.docx)**, ready to edit in Word or Google Docs. For a PDF, export from there.
- **Save and load as JSON** to keep several versions or move between devices
- **Autosave** to your browser's local storage

The layout is a classic single-column resume in Times New Roman.

## How it works

The whole resume is one typed JSON object (`app/types/resumeType.d.ts`). The editor updates it through a small path-based helper built on Immer (`app/hooks/useUpdateState.ts`), so every input writes to a path like `sections.0.subSections.1.role`.

The same object drives both outputs:

- `PreviewPanel` renders it as HTML for the on-screen preview.
- `docToDocx` builds a native Word document with the [`docx`](https://docx.js.org) library, not an HTML conversion, so the downloaded file stays cleanly editable.

## Run locally

Needs Node.js 20 or later.

```sh
npm install
npm run dev
```

Then open http://localhost:3000.

## Tech

Next.js 16, React 19, TypeScript, Tailwind CSS, Immer, docx.

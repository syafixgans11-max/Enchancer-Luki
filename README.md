# 🎨 Pixcraft Studio

> **Modern, High-Performance Image Studio & AI Enhancement Workspace**  
> Built with React 19, TypeScript, Vite, Tailwind/CSS Variables, Sharp, and Vercel Serverless Architecture.

[![Live Demo](https://img.shields.io/badge/Demo-Live%20Preview-brightgreen?style=for-the-badge&logo=vercel)](https://pixcraft-studio.vercel.app)
[![Node Version](https://img.shields.io/badge/Node-%3E%3D20.0.0-blue?style=for-the-badge&logo=node.js)](https://nodejs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-8.3-646CFF?style=for-the-badge&logo=vite)](https://vitejs.dev)

---

## 🌟 Overview

**Pixcraft Studio** is a commercial-grade web-based image manipulation suite offering a hybrid workflow:
1. **Client-Side Core (Zero Latency & Privacy-First)**: Processing operations such as cropping, rotating, multi-frame composing, targeted compression, format conversions, filters, color balance, and watermarking run 100% locally in the browser utilizing modern Canvas and Web Workers.
2. **Serverless AI Cloud Services**: Heavy-duty AI features (AI Outpainting / Canvas Expansion, Background Removal, Watermark Erasing, and Object Removal via Inpainting) run seamlessly via serverless backend pipelines with high-fidelity local fallback engines.

---

## ✨ Features

### 🧠 AI Cloud Suite
- **AI Outpainting (Expand)**: Extend image canvas and scenery to standard aspect ratios (`1:1`, `16:9`, `9:16`, `4:3`, `3:4`) or custom dimensions with intuitive drag-and-drop repositioning and interactive corner handles.
- **Smart Background Removal**: Clean cutout with smooth alpha feathering.
- **Magic Watermark Eraser**: Specialized automated watermark and artifact removal.
- **Object Inpainting Remover**: Interactive brush, rectangle, and lasso mask selector with multi-tier failover and guaranteed original pixel lock.
- **High-Definition Upscaler**: Lanczos3 multi-pass resolution upscaling (2x / 4x).

### 🛠️ Client-Side Studio Tools
- **Composer (2–5 Frames)**: Multi-photo layout grid, dynamic dividers, border customization, and frame-specific filters.
- **Target KB Compressor**: Intelligent iterative compression to meet exact file-size thresholds (WebP/JPEG/PNG).
- **Pro Color Grading**: Exposure, contrast, saturation, vibrance, highlights, shadows, and vintage/cinematic presets.
- **Batch Processing & Presets**: Apply recipes across multiple images simultaneously and export directly to a single ZIP.
- **State Management & Undo/Redo**: 50-step undo/redo stack, original image preservation, and comparison slider.
- **Offline Capable & PWA-Ready**: Cached assets allow offline operations once loaded.

---

## 🏗️ Project Architecture

```
pixcraft/
├── api/                    # Vercel Serverless Function Endpoints
│   ├── ai.ts               # Core AI router (expand, inpaint, upscale, removebg, removewm)
│   ├── auth.ts             # JWT token authentication & access verification
│   ├── health.ts           # System status & environment health checks
│   └── images.ts           # Image upload & temporary asset handler
├── server/                 # Backend Engines & Fallback Processors
│   ├── core.ts             # Sharp pipelines, memory limits, and security validators
│   ├── ezremove.ts         # Fast AI object removal integration
│   ├── gradioUpscaler.ts   # PLKSR deep-learning super-resolution client
│   ├── imageExpand.ts      # FLUX.1 Fill Outpainting & ambient local diffusion
│   ├── inpainting.ts       # LaMa architecture & boundary-preserving inpainting
│   └── magicEraser.ts      # Cloud watermark detection & removal client
├── src/                    # Frontend React 19 Application
│   ├── components/         # Studio UI components (Canvas, Toolbars, Composer, Landing)
│   ├── studio/             # Business logic, Web Workers, state stores, recipe validation
│   ├── engine.ts           # Browser-side canvas rendering & image conversions
│   ├── StudioApp.tsx       # Main Studio application root
│   └── main.tsx            # React bootstrap & theme provider
├── public/                 # Static assets, icons, manifest, and media previews
├── docs/                   # Architectural guides, deployment instructions, and QA specs
├── tests/                  # Unit and integration test suites
├── server.ts               # Local full-stack development server
└── vercel.json             # Vercel deployment routing & header configuration
```

---

## 🚀 Quick Start & Installation

### Requirements
- **Node.js** `>= 20.0.0` or **Bun** `>= 1.1.0`
- **npm**, **pnpm**, or **bun**

### 1. Clone Repository
```bash
git clone https://github.com/rhmt-ofc/pixcraft.git
cd pixcraft
```

### 2. Install Dependencies
```bash
bun install
# or
npm install
```

### 3. Setup Environment Variables
```bash
cp .env.example .env.local
```
*(Optional)* Add API keys if you wish to use remote cloud providers for upscaling or background removal. If left blank, the application automatically uses built-in high-performance Sharp local engines.

### 4. Run Development Server
```bash
npm run dev
# or
bun run dev
```
Open **`http://localhost:3000`** in your browser.

---

## 📦 Production Build & Deployment

### Build for Production
```bash
npm run build
```
This compiles TypeScript (`tsc --noEmit`) and packages the frontend with Vite into `dist/`.

### Deploy to Vercel
Pixcraft is preconfigured for zero-config Vercel deployment:
1. Push to your GitHub repository.
2. Import the project into Vercel.
3. Set the Framework Preset to **Vite**.
4. The backend serverless functions in `/api` are automatically detected and deployed.

---

## 📄 License & Commercial Rights

Copyright (c) 2026 Pixcraft Studio. All rights reserved.

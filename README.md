# 3D Gallery Photography Template

A cinematic, infinite-scrolling 3D photography gallery. Your photos float as curved WebGL planes along a depth tunnel — scroll (mouse wheel, arrow keys, or touch) to glide through them in a continuous loop, with soft focus falloff and auto-play that resumes after 3 seconds of inactivity.

Perfect as a portfolio or showcase template for photographers, designers, and visual artists.

## Features

- **Infinite 3D scroll** — images arranged as planes along the Z-axis in a seamless wrapping loop; scrolling moves the camera through them forever
- **Curved, depth-aware planes** — each photo is a subtly curved plane (32×32 segments) with distance-based falloff: focused up close, softly blurred far away
- **Multiple input modes** — mouse wheel, arrow keys, touch, plus drag; smooth velocity-based motion with damping
- **Auto-play with idle resume** — gallery drifts on its own; pauses while you interact and resumes after 3s idle
- **Post-processing polish** — bloom and vignette effects via `@react-three/postprocessing`
- **Customizable props** — `speed`, `zSpacing`, `visibleCount`, `falloff` (near/far), fade and blur settings, per-plane styling
- **Hero overlay** — mix-blend title overlay ("I create; therefore I am") and control hints, themed light/dark via `next-themes`

## Tech Stack

- [Next.js 15](https://nextjs.org) (App Router, Turbopack) + React 19 + TypeScript
- [three.js](https://threejs.org) via [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber), [@react-three/drei](https://github.com/pmndrs/drei), and [@react-three/postprocessing](https://github.com/pmndrs/react-postprocessing)
- [Tailwind CSS 4](https://tailwindcss.com) + `next-themes`
- [Lucide](https://lucide.dev) icons
- Originally generated with [v0.app](https://v0.app)

## Quick Start

```bash
# install
npm install

# dev server
npm run dev
# open http://localhost:3000
```

Build for production:

```bash
npm run build
npm start
```

## Customizing

Swap in your own photos: drop image files into `public/` and update the `sampleImages` array in `app/page.tsx`. Then tune the motion:

```tsx
<InfiniteGallery
  images={myImages}
  speed={1.2}                 // base auto-play speed
  zSpacing={3}                // depth gap between planes
  visibleCount={12}           // planes rendered at once
  falloff={{ near: 0.8, far: 14 }}  // focus falloff range
/>
```

## Project Structure

```
3-d-gallery-photography-template/
├── app/
│   ├── page.tsx        # Home — image list + InfiniteGallery config + overlay
│   ├── layout.tsx      # Root layout (theme provider)
│   └── globals.css     # Tailwind base styles
├── components/
│   ├── InfiniteGallery.tsx   # The 3D infinite-scroll gallery (core)
│   └── theme-provider.tsx
└── public/
    ├── 1.webp … 8.webp       # Sample gallery images
    └── placeholder.*         # Placeholder assets
```

## Environment Variables

None required. All rendering is client-side in the browser.

## Deployment Notes

This is a Next.js App Router application (no static export configured), so it needs a Node.js server runtime such as [Vercel](https://vercel.com) or [Netlify](https://netlify.com):

```bash
npm install
npm run build
npm start
```

---

Built by Girish Lade · https://ladestack.in

# Tech Stack Research

## Current Stack
- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Backend**: Node.js, Express, PostgreSQL
- **Infrastructure**: AWS, Docker, GitHub Actions
- **Testing**: Vitest, Playwright, Jest

## Evaluating for Next Project

### Frontend Frameworks
**Astro**
- Pros: Fast, content-focused, partial hydration
- Cons: Limited for highly interactive apps
- Verdict: Great for marketing sites

**SvelteKit**
- Pros: Simple, performant, less boilerplate
- Cons: Smaller ecosystem
- Verdict: Worth trying for next side project

**Next.js 14**
- Pros: Full-stack framework, great DX, Server Components
- Cons: Can be complex, vendor lock-in concerns
- Verdict: Still the safe choice

### State Management
- Zustand: Lightweight, simple API ⭐
- Jotai: Atomic approach, interesting
- TanStack Query: Essential for server state

### Backend Alternatives
**Bun**
- Native TypeScript support
- Built-in test runner
- Faster than Node.js
- ✅ Recommended to try

**Deno**
- Secure by default
- Great standard library
- ⚠️ Ecosystem still catching up

## Decision
Going with React + Zustand + Bun for next project

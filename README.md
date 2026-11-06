# Fey

A parent-mediated companion with voice, text, and AAC.

> Fey is the product. **TMAPP** is the internal name used in the spec and the code packages (`@tmapp/*`).

**Status: internal prototype, synthetic data only.** No real family data is processed, and external family testing is blocked by the release gates in section 22 of the spec.

## What Fey is

- A child companion that takes turns by voice, text, or AAC, with a one-tap break control and low sensory load.
- An explicit personalization profile controlled by the parent. Fey does not infer traits.
- A weekly plan the parent reviews and approves. If the parent doesn't review it, the last approved plan continues.

Fey is not a diagnostic, assessment, or clinical tool.

## Documentation

- [`docs/TMAPP-master-spec.md`](docs/TMAPP-master-spec.md): the single source of truth for product, architecture, and release gates
- [`docs/BUILD-GUIDE.md`](docs/BUILD-GUIDE.md): step-by-step build guide, derived from the spec

## Quick start

Requires Node 22+ and pnpm.

```bash
pnpm install
pnpm check   # strict typecheck, unit tests, prohibited-claims check, RLS check
```

## Repository layout

| Path | Purpose |
|---|---|
| `packages/strings` | All user-facing copy and the prohibited-claims list |
| `packages/consent` | Consent purposes, defaults, and revocation effects |
| `packages/config` | Release gates, environment guard, age bands |
| `packages/action-registry` | Closed, versioned actions for weekly plans |
| `packages/companion` | Model payload allowlist, break and turn state machine, sensory defaults |
| `tooling/checks` | CI checks for claims and row-level security |
| `supabase/` | Database migrations and Edge Functions |
| `apps/mobile` | iOS app (not yet created) |

## Ground rules

1. Synthetic data only until every gate in spec section 22 closes.
2. Copy lives in `packages/strings` so CI can check it.
3. Secrets stay server-side. The app never holds a model API key.
4. Run `pnpm check` before every commit.

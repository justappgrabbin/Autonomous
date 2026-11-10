# special-fishstick source audit — first executable checks

Original source: [Drive ZIP](https://drive.google.com/file/d/1SrrTrBITHKT1FW5w9wGkM2crBaDcfz6M/view)
Preserved archive: `imports/special-fishstick-main.zip.b64.part000` through `part014` on this branch.

## Checks performed

- ZIP extraction succeeds; 107 archive entries.
- Node v22.16.0 and npm v10.9.2 were available in the inspection environment.
- `npm run check` fails immediately: **TS18003**, because `tsconfig.json` includes `client/src/**/*`, `shared/**/*`, `server/**/*`, but the ZIP puts most React files at its root and does not contain those three expected directories.
- `package.json` defines `dev` and `build` using `server/index.ts`; the archive does **not** include this file.
- `App.tsx` imports `@/components/ui/*` and other `@/components/*` files; the archive has no `client/src` component tree or `components/ui` directory.
- `vite.config.ts` sets Vite root to `client` and aliases `@` to `client/src`, which do not exist in the ZIP.
- `AutonomyControlCenter.tsx` persists an enabled flag and proposals via `localStorage`; no verified background execution connection was established.
- `Terminal.tsx` explicitly identifies several commands as simulated, including process and file operations.
- `lib/AIService.ts` contains external API request paths and an Ollama HTTP path. Availability, authentication, security and local execution are **not** verified.
- `main.py` is a minimal script, not an autonomous Python agent.

## Conclusion

**Source preservation: complete as chunked archive. Application build: failing. Autonomous execution: not demonstrated.** This is a potentially useful collection of donor components, not a verified ready-to-run computer.

## Preservation and next engineering tasks

1. Reconstruct original ZIP, compare checksum and retain unchanged original.
2. Build a separate repaired working tree; do not overwrite the original.
3. Resolve actual import locations and missing UI primitives; restore or implement missing server only after checking the intended architecture.
4. Run typecheck, build, runtime smoke tests and test the autonomy-to-execution path, terminal behavior and model connectivity.
5. Integrate verified capabilities into the intended host only after compatibility and regression testing.

No claims of complete autonomy or functioning agent hands are justified by these checks.

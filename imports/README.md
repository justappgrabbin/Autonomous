# Preserved source archive: special-fishstick-main.zip

Source: https://drive.google.com/file/d/1SrrTrBITHKT1FW5w9wGkM2crBaDcfz6M/view

The original ZIP was uploaded losslessly as **15 ordered Base64 text parts**, because the connector rejected a single large binary upload. No source files were intentionally changed or removed.

To restore the ZIP from this branch in a POSIX shell:

```sh
cat imports/special-fishstick-main.zip.b64.part* | base64 -d > special-fishstick-main.zip
unzip -t special-fishstick-main.zip
```

The parts must be concatenated in lexicographic filename order (part000 through part014). Base64 content length: 14,716,740 characters; original Drive file size reported: 11,037,554 bytes.

## Verification status

- Archive preserved as source data on import branch.
- Full source build, runtime execution, tests, and security review: **not verified**.
- Previously observed: React/TypeScript UI, Express-related dependencies, agent and autonomy panels; some features may be incomplete.
- Do not merge into the production computer or claim fully functional autonomy without integration tests.

This import is intentionally isolated from the repository main branch.

# repro-OXDEV-77637-uv-workspace

Temporary QA repro fixture for OXDEV-77637 (SCA drops a transitive CVE that is owned by a
uv workspace member). Root `pyproject.toml` declares `[tool.uv.workspace]`; the vulnerable
package (`starlette 0.25.0`, CVE-2026-48710) is reachable ONLY through the private member
`packages/internal_lib` (`internal-scripts` -> `fastapi==0.92.0` -> `starlette`).

Verified locally with uv 0.12.1:
- full checkout: `uv tree` resolves 11 packages, starlette 0.25.0 present
- lean clone (member dirs omitted): `uv tree` returns a root-only graph, exit code 0, no warning

Expected OX behaviour: starlette 0.25.0 + CVE-2026-48710 must appear in SBOM/Open Source
Security for this manifest. Control fixture (same package, flat manifest, no workspace):
https://github.com/sb-ox/repro-OXDEV-77637-uv-flat

Tag for cleanup: repro-OXDEV-77637 — delete this folder once the ticket is closed.

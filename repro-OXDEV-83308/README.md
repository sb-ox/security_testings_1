# repro-OXDEV-83308

Fixture for OX repro of OXDEV-83308 (GitHub Dependabot findings auto-closed as
"3rd party issue removed" while the upstream alerts are still open).

`requirements.txt` pins known-vulnerable package versions so GitHub Dependabot
raises alerts on this repository. Those alerts are the ground truth that must
stay OPEN while OX is checked for false auto-closes.

Tag: repro-OXDEV-83308 — safe to delete this directory during cleanup.

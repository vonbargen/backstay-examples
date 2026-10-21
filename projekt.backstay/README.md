# Projekt — die Wurzel des Bundles

EinDateiModul S4 (2026-10-08, Entscheide 8, 11, 12). Die Wurzel ist das
**Projekt** mit 0..n Dokumenten: `projekt.json` trägt `$types` (mit `$main`)
und `$files`. `$files` nennt die **ausgegliederten** Felder, hier das
Dokument in `dokument.json`; die Datei trägt ihre Typen selbst (`$types`),
in der Wurzel steht nichts doppelt. Alles andere liegt **inline**: die
Notizen sind eine Collection vom Typ Notiz direkt in `projekt.json` und
damit ein Ziel der Notiz-Geste (»Notiz · Notizen«).

Beim Sichern steht `$types`, dann `$files`, dann die Daten; eine Komponente,
die in der Sitzung entsteht (Notiz am Rückfallort), wird in `$files`
nachgetragen. Ein loses Bundle ohne Wurzel bleibt gültig.

```bash
cargo run -q -p backstay-cli -- validate examples/projekt.backstay
BACKSTAY_SMOKE_SCENARIO=save-roundtrip scripts/smoke.sh examples/projekt.backstay
```

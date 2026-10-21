# Mein erstes Projekt — ein Modul, eine Datei

EinDateiModul S2 (2026-10-08). Das erste eigene Dokument, hier
in der **Ein-Datei-Form**: `dokument.json` trägt unter `$types` das, was
sonst in `dokument.schema.json` steht (Kopf `$main`, `$import`, `$defs`,
`properties`); eine Schema-Datei gibt es nicht. Die Daten folgen nach
`$types`.

`$types` ist eine **Speicherform**: beim Laden spleißt Backstay die
Typen in die Schema-Zelle, der Bauplan-Tab zeigt sie wie bei jedem
anderen Modul, beim Sichern legt der Schreibweg sie zurück. Sichern
eines unveränderten Dokuments ändert kein Byte.

Ein Modul mit Schema-Datei nennt sie seit S2 ausdrücklich
(`"$schema": "x.schema.json"` als erster Schlüssel); `$types` und
`$schema` schließen einander aus.

Prüfen:

```bash
cargo run -q -p backstay-cli -- validate examples/mein-erstes-projekt.backstay
BACKSTAY_SMOKE_SCENARIO=save-roundtrip scripts/smoke.sh examples/mein-erstes-projekt.backstay
```

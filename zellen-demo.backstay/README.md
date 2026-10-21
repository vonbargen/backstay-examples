# Zellen-Demo — Werte sind Datenfelder, der Text referenziert sie (CellReferenz)

Das kleinste Dokument, das die **Zell-Referenz** zeigt: die Zahlen der
Rechnung sind echte, getypte **Datenfelder** (`reihen: 6`,
`pro_reihe: 7`), das Ergebnis ist ein **`$compute`-Feld** (`gesamt`).
Im Text steht nur Prosa — an drei Stellen liegt ein Anker, der eine
dieser Daten-Zellen referenziert.

Öffnen: `cargo run -- examples/zellen-demo.backstay`

## Was drinsteht

Der Satz im Feld „Rechnung" lautet (Datei-Wortlaut):

> Ein Karton fasst **6** Reihen zu je **7** Flaschen, macht
> **zweiundvierzig** Flaschen pro Karton.

Daneben stehen die Felder `reihen = 6`, `pro_reihe = 7` und das
virtuelle Feld `gesamt` mit der Formel
`reihen * pro_reihe`. Darüber liegen drei Anker
(`anchors.json`), alle vom `kind: "cell"`:

| Anker | Wortlaut | Referenz (`body.source`) | Anzeige |
|---|---|---|---|
| `reihen` | `6` | `/reihen` | 6 |
| `pro_reihe` | `7` | `/pro_reihe` | 7 |
| `gesamt` | `zweiundvierzig` | `/gesamt` | **42** |

Die Normal-Sicht zeigt an jeder Referenz den **Wert** der
referenzierten Zelle (Wert-Lesart); der Datei-Text bleibt reine Prosa.
Der Schalter „Darstellung → Wortlaut anzeigen" schaltet auf die Prosa
zurück (die globale Brille — Feldschattierung wird kräftiger, das
Fenster trägt den Untertitel „Wortlaut-Ansicht").

## Was man ausprobiert

**1. Zahlen sind editierbare Zellen.** `reihen` im Formular (oder der
Tabelle) auf `8` stellen: `gesamt` rechnet neu, und die Anzeige im
Text zieht mit — an allen Stellen, die die Zelle referenzieren.

**2. Die Formel.** `gesamt` ist ein `$compute`-Feld im Schema — die
Formel rechnet über `record` (und dürfte über `bundle` in andere
Welten schauen).

**3. Fehlerfall.** Das Feld `reihen` testweise umbenennen oder die
Referenz auf eine tote Adresse zeigen lassen: der Text degradiert zu
seiner lesbaren Prosa (Wortlaut-Fallback) und der Validator meldet die
tote Referenz — nie ein Fehlertext im Dokument.

## Auch im Druck

```
cargo run -- render examples/zellen-demo.backstay
```

gibt „macht **42** Flaschen pro Karton." aus — dieselbe Wert-Lesart
wie in der GUI läuft im Render-Walk (ein Pfad für alle Sichten). Ein
Anker mit `render: "text"` würde stattdessen seinen Prosa-Wortlaut
drucken (deklariertes Druckbild).

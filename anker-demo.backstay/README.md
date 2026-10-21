# Anker-Demo

Die vier Ankertypen am ganzen Feld (ToDo JsAnker). Ein Feld ohne Anker ist
ein Literal. Ein Anker am Feld sagt, woher sein Wert kommt. Der Ausdruck
steht im Anker (`anchors.json`), im Feld (`anker_demo.json`) steht das
Ergebnis.

| Feld           | Ankertyp | Im Anker                             | Im Feld          |
|----------------|----------|--------------------------------------|------------------|
| `gesamt`       | JS       | `reihen * pro_reihe`   | `42`             |
| `reihen_kopie` | Adresse  | `/reihen`                 | `6`              |
| `karton_namen` | Query    | `$.anker_demo.kartons[*].name`       | `["Rot","Weiß"]` |
| `quelle`       | URI      | `https://example.org/weinkarton`     | dieselbe URI     |

Dazu Formel und Query an einer **Textstelle** (Feld `satz`): der Anker
bezieht sich auf eine Wortfolge im Text. Gespeichert bleibt der Wortlaut
(»zweiundvierzig«, »Rot«); in der Anzeige und im Druck steht an seiner
Stelle das Ergebnis (»42«, der Name des ersten Kartons). `record` ist der
Record des Feldes. Eine Query im Text muss genau eine Stelle treffen.

Ein Feld, dessen Wert ein Anker bestimmt, ist grau. Einsetzen und
Ausschneiden auf einem solchen Feld werden mit einer Meldung abgewiesen.

Prüfen:

```bash
cargo run -q -p backstay-cli -- validate examples/anker-demo.backstay
```

Ändert man `reihen` in der Datei von Hand auf 5, meldet `validate`, dass
`gesamt` und `reihen_kopie` nicht mehr das Ergebnis tragen. Öffnen und
Sichern in Backstay bringt die Datei auf Stand.

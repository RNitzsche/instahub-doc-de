# CRUD

#### Aufgabe 7.1 Was ist CRUD? {-}

_Recherchieren_ Sie, was unter CRUD im Zusammenhang mit Datenbanken verstanden wird!

## INSERT - Datensätze einfügen

_Überlegen_ Sie, was der folgende SQL-Befehl vermutlich tun wird!

```sql
INSERT
INTO users (
  username, 		email,		 		password, 
  name,				bio, 				gender,
  birthday,    		city, 	   			country, 
  centimeters, 		avatar,    			role, 
  is_active,   		remember_token,		created_at, 
  updated_at
) 
VALUES	(
  'guenther37',     'guenther@instahub.app',	'12345',
  'Günther Müller',	'Günther mag Kartoffelsalat.', 'male',
  '2006-06-06 00:00:00', 'Leipzig',		'Deutschland',
  '173',			'avatar.png',		'user',
  '0',	    		NULL,	    		now(), 
  now()
)
```

#### Aufgabe 7.2 Ihr erstes Insert {-}

1. _Geben_ Sie den obigen Befehl ein.
2. _Überprüfen_ Sie das Ergebnis.
3. _Erklären_ Sie, was `now()` bedeutet! (Tipp: Sehen Sie sich an, was in den beiden Spalten in der Tabelle steht!)

#### Aufgabe 7.3 Noch ein paar Inserts {-}

1. _Fügen_ Sie einen Datensatz für Joachim Löw mit allen leicht öffentlich zugänglichen Daten in die Datenbank ein!
2. _Fügen_ Sie einen weiteren Datensatz für eine Person Ihrer Wahl in die Datenbank ein!

#### Aufgabe 7.4 Spezialaufgabe {-}

_Überlegen_ Sie, warum das Feld `id` nicht eingetragen wurde und dennoch gefüllt wurde!

## UPDATE - Datensätze verändern

Um Datensätze zu verändern, gibt es den Befehl `UPDATE`. In einer SQL-Referenz finden Sie folgende Beschreibung:

----

``UPDATE``  *< table_name >*

``SET`` *< column1 >* `=` *< value1 >*`, ` *< column2 >* `=` *< value2 >*`,` *...*

`WHERE` *< condition >*`; `

-----

Dabei müssen Sie alle in `Schreibmaschinenschrift` geschriebenen Texte *exakt* so eingeben, wie Sie da stehen. Texte in *< spitzen Klammern >* sind Platzhalter und sollen von Ihnen durch konkrete Inhalte ersetzt werden. Die `WHERE`-Klausel kennen Sie bereits aus dem `SELECT`-Befehl. Und sie funktioniert hier sogar genauso. ;-)

**ACHTUNG:** Sie können mit einem einzigen `UPDATE`-Befehl viel Unheil anrichten. Wenn Ihnen etwas passiert ist, kontaktieren Sie Ihre Lehrkraft, sie kann Ihre Datenbank zurücksetzen.

#### Aufgabe 7.5 Update {-}

_Erstellen_ Sie jeweils ein UPDATE-Kommando:

1. Alle weiblichen Nutzerinnen sollen 160&nbsp;cm groß sein.
2. Statt "Germany" soll es im Feld `country` immer "Deutschland" heißen.
3. _Ersetzen_ Sie die Körpergröße bei allen Dresdnern mit dem Wert `FLOOR(RAND()*45)+150`.
   1. _Ermitteln_ Sie, was dieser Befehl bewirkt hat!
   2. _Recherchieren_ Sie, was es mit den Funktionen `FLOOR` und  `RAND` auf sich hat!
4. _Aktivieren_ Sie den Account von Jogi Löw. (Tipp: Überlegen Sie, welche Spalte für die Aktivierung eines Accounts zuständig sein mag.)
5. _Ersetzen_ Sie die Körpergröße bei allen Münchnern mit einen zufälligen Wert zwischen 130&nbsp;cm und 190&nbsp;cm!

## DELETE - Datensätze löschen

*Suboptimal*
Um Datensätze zu löschen, gibt es den Befehl `DELETE`. In einer SQL-Referenz finden Sie folgende Beschreibung:

------

``DELETE FROM``  *< table_name >*

`` WHERE`` *< condition >*`; `

------

Die `WHERE`-Klausel kennen Sie bereits aus dem `SELECT`- und dem `UPDATE`-Befehl. 

**Achtung:** _Vor_ dem Absetzen eines `DELETE`-Kommandos sollte man immer die verwendete `WHERE`-Klausel in einem `SELECT`-Kommando ausprobieren.

#### Aufgabe 7.6 Delete {-}

_Erstellen_ Sie jeweils ein DELETE-Kommando:

1. _Löschen_ Sie alle nicht aktivierten Accounts.
2. _Löschen_ Sie Jogi Löw.

## Grenzen von CRUD

Kaufleute müssen Ihre Geschäfte in Handelsbüchern dokumentieren (Buchhaltung). Heute werden diese Bücher in der Regel nicht auf Papier, sondern in Datenbanken geführt. Im Handelsgesetzbuch wird im §239 Absatz 3 bestimmt:

> Eine Eintragung oder eine Aufzeichnung darf nicht in einer Weise 
> verändert werden, daß[!] der ursprüngliche Inhalt nicht mehr feststellbar 
> ist. [...]

**Beispiel: ** Wenn die Bank auf Grund eines Fehlers von Ihrem Konto Geld abbucht und ihren Fehler danach korrigiert, ist die Bank verpflichtet, den Fehler nicht unkenntlich zu machen:

| Text                                                | Datum      | Betrag         | Saldo          |
| --------------------------------------------------- | ---------- | --------------: | --------------: |
| DB Hamburg <br />Fahrkarte | 22.05.20 | 19,80- | 10,03+ |
| Barabhebung<br />Kiel Hbf         | 22.05.20 | 5.052.202,00- | 5.052.192,00- |
| Storno <br />Wir bitten unser <br />Versehen zu ent-<br />schuldigen | 27.05.20 | 5.052.202,00+  | 10,03+        |

#### Aufgabe 7.7 Darf der das...? {-}
1. _Begründen_ Sie, warum eine vollständige Unterstützung von CRUD in der Buchhaltung nicht zulässig ist.
2. _Finden_ Sie Beispiele für Daten, bei denen Sie _vermuten_, dass sie ebenfalls nicht ohne weiteres verändert oder gelöscht werden dürfen.

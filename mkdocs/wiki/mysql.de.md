---
category: wiki
sub_category_1: mysql
sub_category_2: commands
language: de
tags:
- wiki
- mysql
- commands
---

## Maximale Anzahl von gleichzeitigen Verbindungen
In MySQL können Sie die maximale Anzahl von gleichzeitigen Verbindungen mit der folgenden Abfrage ermitteln:

```sql
SHOW VARIABLES LIKE 'max_connections';
```

Diese Abfrage gibt das maximale Limit für die Anzahl der Verbindungen zurück, die zur gleichen Zeit auf den MySQL-Server zugreifen können. Beachten Sie jedoch, dass dieses Limit von der Konfiguration des MySQL-Servers abhängt und nicht unbedingt der tatsächlichen Anzahl von gleichzeitigen Transaktionen entspricht, die ausgeführt werden können.

## Aktuelle Anzahl von Verbindungen

Um die aktuelle Anzahl von Verbindungen anzuzeigen, die zu einem bestimmten Zeitpunkt auf den MySQL-Server zugreifen, können Sie die folgende Abfrage verwenden:

```sql
SHOW STATUS WHERE `variable_name` = 'Threads_connected';
```

Diese Abfrage gibt die Anzahl der aktiven Verbindungen zurück, die auf den MySQL-Server zugreifen. Beachten Sie jedoch, dass die Anzahl der Verbindungen schwanken kann, da Verbindungen geöffnet und geschlossen werden, während die Datenbank verwendet wird.

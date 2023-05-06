---
category: laravel
sub_category_1: queue
sub_category_2: worker
language: de
tags:
- laravel
- forge
- queue
- worker
---

# Laravel Forge queue worker

Hier ein paar Tipps und Tricks zum Laravel Forge queue worker.

## Maximum Seconds Per Job

Die Option "Maximum Seconds Per Job" ist eine Einstellung, die bei der Konfiguration eines Workers in Forge verfügbar ist. Sie gibt an, wie viel Zeit ein Worker maximal für die Ausführung einer einzelnen Aufgabe (Job) aufwenden darf.

In vielen Fällen ist es wichtig, dass Aufgaben schnell und zuverlässig ausgeführt werden, um die Leistung der Anwendung zu maximieren und sicherzustellen, dass Benutzer eine gute Erfahrung machen. Gleichzeitig können einige Aufgaben jedoch sehr zeitaufwändig sein und den Worker blockieren, was dazu führt, dass andere Aufgaben nicht ausgeführt werden können. Die Option "Maximum Seconds Per Job" hilft, dieses Problem zu lösen, indem sie sicherstellt, dass eine einzelne Aufgabe nicht zu lange dauert.

Die "Maximum Seconds Per Job"-Einstellung gibt an, wie lange der Worker maximal für die Ausführung einer einzelnen Aufgabe aufwenden darf. Wenn die Aufgabe innerhalb dieser Zeit abgeschlossen wird, wird der Worker die Ergebnisse zurückgeben und auf die nächste Aufgabe warten. Wenn die Aufgabe jedoch länger als die angegebene Zeit dauert, wird der Worker die Aufgabe abbrechen und auf die nächste Aufgabe warten.

Diese Einstellung ist nützlich, um sicherzustellen, dass der Worker effizient arbeitet und nicht blockiert wird. Wenn Aufgaben sehr unterschiedlich in ihrer Dauer sind, kann es jedoch schwierig sein, eine geeignete "Maximum Seconds Per Job"-Einstellung zu wählen. In diesem Fall kann es erforderlich sein, die Einstellung anzupassen oder mehrere Worker zu verwenden, um sicherzustellen, dass alle Aufgaben schnell und zuverlässig ausgeführt werden.

## Rest Seconds When Empty

Die Option "Rest Seconds When Empty" bezieht sich auf eine Einstellung, die bei der Konfiguration eines Workers in Forge verfügbar ist. Diese Einstellung gibt an, wie lange ein Worker pausieren soll, wenn er keine Aufgaben auszuführen hat.

Wenn ein Worker keine Aufgaben hat, kann er unnötigerweise Ressourcen verbrauchen, indem er CPU-Zyklen und Arbeitsspeicher verwendet, um nach neuen Aufgaben zu suchen. Um dies zu vermeiden, kann der "Rest Seconds When Empty" -Parameter verwendet werden, um den Worker anzuweisen, für eine bestimmte Zeit zu pausieren, bevor er erneut nach neuen Aufgaben sucht.

Die "Rest Seconds When Empty"-Einstellung wird normalerweise in Sekunden angegeben und kann je nach Anwendungsfall angepasst werden. Wenn zum Beispiel der Worker Aufgaben hat, die sehr häufig eintreffen, könnte es sinnvoll sein, eine relativ kurze Ruhezeit einzustellen, um sicherzustellen, dass der Worker schnell auf neue Aufgaben reagieren kann. Andererseits, wenn der Worker nur gelegentlich Aufgaben erhält, könnte es sinnvoll sein, eine längere Ruhezeit einzustellen, um Ressourcen zu sparen und die Kosten zu reduzieren.

## Graceful Shutdown Seconds

Die Option "Graceful Shutdown Seconds" ist eine Einstellung, die bei der Konfiguration eines Workers in Forge verfügbar ist. Sie gibt an, wie viel Zeit dem Worker zur Verfügung steht, um laufende Aufgaben abzuschließen, bevor er heruntergefahren wird.

In einigen Fällen kann es notwendig sein, einen Worker herunterzufahren, beispielsweise wenn eine neue Version der Anwendung bereitgestellt wird oder wenn der Worker nicht mehr benötigt wird. Wenn der Worker jedoch während der Ausführung einer Aufgabe heruntergefahren wird, kann dies zu unerwarteten Fehlern oder Datenverlust führen. Um dies zu vermeiden, gibt es die Option "Graceful Shutdown Seconds".

Diese Einstellung gibt an, wie viel Zeit der Worker haben soll, um laufende Aufgaben abzuschließen, bevor er heruntergefahren wird. Der Worker setzt den "Shutdown"-Prozess in Gang, indem er neue Aufgaben ablehnt und dann auf das Ende der laufenden Aufgaben wartet. Wenn die Zeit, die in der "Graceful Shutdown Seconds"-Einstellung angegeben ist, abgelaufen ist, beendet der Worker alle noch laufenden Aufgaben und wird anschließend heruntergefahren.

Die "Graceful Shutdown Seconds"-Einstellung ist optional, da es in einigen Fällen nicht erforderlich sein kann, dass der Worker Aufgaben vor dem Herunterfahren abarbeitet. Wenn jedoch eine solche Einstellung erforderlich ist, kann dies dazu beitragen, dass der Worker heruntergefahren wird, ohne dass es zu Fehlern oder Datenverlust kommt.

## Das Zusammenspiel zwischen "Graceful Shutdown Seconds" und "Maximum Seconds Per Job"

Das Zusammenspiel zwischen "Graceful Shutdown Seconds" und "Maximum Seconds Per Job" kann wichtig sein, da sie beide dazu beitragen können, sicherzustellen, dass ein Worker zuverlässig arbeitet und Aufgaben schnell und effizient ausführt.

Wenn der "Graceful Shutdown Seconds" Wert zu niedrig ist, besteht das Risiko, dass der Worker nicht genügend Zeit hat, um laufende Aufgaben ordnungsgemäß abzuschließen, bevor er heruntergefahren wird. Wenn andererseits der "Maximum Seconds Per Job" Wert zu hoch ist, besteht das Risiko, dass der Worker für zu lange Zeit an einer einzelnen Aufgabe arbeitet und dadurch andere Aufgaben blockiert und der Durchsatz sinkt.

Eine gute Praxis ist es, die "Maximum Seconds Per Job" Einstellung so zu wählen, dass die meisten Aufgaben in der Regel innerhalb dieser Zeit abgeschlossen werden können. Wenn jedoch eine Aufgabe länger als diese Zeit dauert, sollte der "Graceful Shutdown Seconds" Wert so gesetzt sein, dass der Worker genügend Zeit hat, um die laufende Aufgabe abzuschließen, bevor er heruntergefahren wird.

Es ist jedoch auch wichtig zu beachten, dass es in einigen Fällen sinnvoll sein kann, eine höhere "Maximum Seconds Per Job"-Einstellung zu wählen, wenn es sich um komplexe oder ressourcenintensive Aufgaben handelt. In diesem Fall sollte der "Graceful Shutdown Seconds" Wert entsprechend angepasst werden, um sicherzustellen, dass der Worker genügend Zeit hat, um diese Aufgaben zu beenden.

---

Offizielle Dokumentation von Forge:

- Creating A Queue Worker: [Forge - creating-a-queue-worker](https://forge.laravel.com/docs/1.0/sites/queues.html#creating-a-queue-worker)
- Forge ddocumentation: [Forge introduction](https://forge.laravel.com/docs/1.0/introduction.html)

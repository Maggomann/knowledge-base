---
category: phpstan
sub_category_1: commandos
language: de
tags:
- phpstan
- commandos
---

# phpstan

PHPStan ist ein Tool für statische Code-Analyse in PHP. Es überprüft den Code auf Typfehler, unbeabsichtigte Seiteneffekte und andere potenzielle Fehlerquellen. PHPStan bietet Entwicklern eine höhere Code-Qualität und hilft dabei, potenzielle Fehler im Code zu finden, bevor sie in der Produktion auftreten. Das Tool nutzt dabei eine Kombination aus Typ-Inferenz und statischer Analyse, um sicherzustellen, dass der Code typsicher ist und bestimmten Coding-Standards entspricht. Es ist auch eine Erweiterung von PHP und kann in der Entwicklungsumgebung oder als Teil von Continuous Integration/Continuous Deployment (CI/CD) Pipelines verwendet werden, um sicherzustellen, dass der Code in jeder Phase der Entwicklung korrekt funktioniert.

## Kommandos

### phpstan: Der tägliche Wahnsinn

```bash
vendor/bin/phpstan clear-result-cache --memory-limit=5G
vendor/bin/phpstan analyse --ansi --memory-limit=5G
vendor/bin/phpstan --generate-baseline --memory-limit=5G
```

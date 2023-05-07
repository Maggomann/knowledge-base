---
category: phpstan
sub_category_1: commandos
language: en
tags:
- phpstan
- commandos
---

# phpstan

PHPStan is a tool for static code analysis in PHP. It checks the code for type errors, unintended page effects and other potential sources of errors. PHPStan provides developers with higher quality code and helps find potential errors in the code before they occur in production. The tool does this by using a combination of type inference and static analysis to ensure that code is type-safe and meets certain coding standards. It is also an extension of PHP and can be used in the development environment or as part of Continuous Integration/Continuous Deployment (CI/CD) pipelines to ensure that code works correctly at every stage of development.

## Commands

### phpstan: The daily madness

```bash
vendor/bin/phpstan clear-result-cache --memory-limit=5G
vendor/bin/phpstan analyse --ansi --memory-limit=5G
vendor/bin/phpstan --generate-baseline --memory-limit=5G
```

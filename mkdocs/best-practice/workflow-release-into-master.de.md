---
category: github-workflow
sub_category_1: workflow-release-into-master
language: de
tags:
- git
- github
- best-practice
- pull-request
- workflow-release-into-master
---

## Workflow release into master

Dies ist eine von vielen möglichen Methoden, um den Release in den Master-Branch zu integrieren. Der Vorteil dieser Methode besteht darin, dass sowohl die lokalen als auch die Origin-Branches auf den neuesten Stand gebracht werden

1. Checkout des Dev-Release-Branches
2. Pullen der Änderungen vom Upstream-Release-Branch in den lokalen Dev-Release-Branch
3. Commiten der Änderungen im lokalen Dev-Release-Branch
4. Pushen des Dev-Release-Branches in den Origin-Release-Branch
5. Checkout des Dev-Master-Branches
6. Pullen der Änderungen vom Upstream-Master-Branch in den lokalen Dev-Master-Branch
7. Commiten der Änderungen im lokalen Dev-Master-Branch
8. Pushen des Dev-Master-Branches in den Origin-Master-Branch
9. Erstellen eines neuen Branches mit dem Namen "release-into-master", der auf dem Dev-Master-Branch basiert, und Checkout des neuen Branches
10. Pullen der Änderungen vom Origin-Release-Branch in den neuen Branch "release-into-master"
11. Pushen des neuen Branches "release-into-master" in den Origin-Release-Into-Master-Branch
12. Erstellen eines Pull Requests, um die Änderungen vom Dev-Release-Branch in den Dev-Master-Branch zu übertragen

```mermaid
sequenceDiagram
    participant Dev
    participant Upstream
    participant Origin
    Dev ->>+ Upstream: Checkout Dev/Release Branch
    Upstream -->>- Dev: Send Changes for Dev/Release Branch
    Dev ->>+ Dev: Pull from Upstream/Release into Dev/Release Branch
    Dev ->>+ Dev: Commit Changes in Dev/Release Branch
    Dev ->>+ Origin: Push Dev/Release Branch to Origin/Release
    Dev ->>+ Upstream: Checkout Dev/Master Branch
    Upstream -->>- Dev: Send Changes for Dev/Master Branch
    Dev ->>+ Dev: Pull from Upstream/Master into Dev/Master Branch
    Dev ->>+ Dev: Commit Changes in Dev/Master Branch
    Dev ->>+ Origin: Push Dev/Master Branch to Origin/Master
    Dev ->>+ Dev: Create Release-into-Master Branch based on Dev/Master Branch
    Dev ->>+ Dev: Checkout Dev/Release-into-Master Branch
    Dev ->>+ Origin: Pull from Origin/Release into Dev/Release-into-Master Branch
    Dev ->>+ Origin: Push Dev/Release-into-Master Branch to Origin/Release-into-Master
    Dev ->>+ Origin: Create Pull Request to merge Origin/Release-into-Master Branch into Upstream/Master Branch
```

---
category: github
sub_category_1: github-key
language: de
tags:
- composer
- github
- github-key
---

Sie können einen Pull-Request oder Branch mit einem Issue verknüpfen, um anzuzeigen, dass eine Behebung in Bearbeitung ist, und um das Issue automatisch zu schließen, wenn der Pull-Request oder Branch zusammengeführt wird.

**Hinweis:** Die speziellen Schlüsselwörter in einer Pull-Request-Beschreibung werden interpretiert, wenn die Pull-Request auf den _Default_ - Branch des Repositorys abzielt. Wenn die Basis des PR jedoch _ein anderer Zweig_ ist, werden diese Schlüsselwörter ignoriert, es werden keine Links erstellt und das Zusammenführen des PR hat keine Auswirkung auf die Ausgaben. **Wenn Sie einen Pull-Request über ein Schlüsselwort mit einem Issue verknüpfen möchten, muss sich der PR auf dem Standard-Branch befinden.**

## [](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#about-linked-issues-and-pull-requests)Über verknüpfte Probleme und Pull-Requests

Sie können ein Problem manuell mit einer Pull-Anforderung verknüpfen oder ein unterstütztes Schlüsselwort in der Beschreibung der Pull-Anforderung verwenden.

Wenn Sie eine Pull-Anforderung mit dem Problem verknüpfen, auf das sich die Pull-Anforderung bezieht, können Mitbearbeiter sehen, dass jemand an dem Problem arbeitet.

Wenn Sie einen verknüpften Pull-Request mit dem Standard-Branch eines Repositorys zusammenführen, wird das verknüpfte Issue automatisch geschlossen. Weitere Informationen zum Standard-Zweig finden Sie unter „ [Ändern des Standard-Zweigs](https://docs.github.com/en/github/administering-a-repository/changing-the-default-branch) “.

## [](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword)Verknüpfen einer Pull-Anforderung mit einem Problem mithilfe eines Schlüsselworts

Sie können eine Pull-Anforderung mit einem Problem verknüpfen, indem Sie ein unterstütztes Schlüsselwort in der Beschreibung der Pull-Anforderung oder in einer Commit-Nachricht verwenden. Die Pull-Anfrage **muss sich** im Standard-Branch befinden.

-   nah dran
-   schließt
-   abgeschlossen
-   Fix
-   behebt
-   Fest
-   beschließen
-   beschließt
-   aufgelöst

Wenn Sie ein Schlüsselwort verwenden, um auf einen Pull-Request-Kommentar in einem anderen Pull-Request zu verweisen, werden die Pull-Requests verknüpft. Durch das Zusammenführen der referenzierenden Pull-Anforderung wird auch die referenzierte Pull-Anforderung geschlossen.

Die Syntax zum Schließen von Schlüsselwörtern hängt davon ab, ob sich das Problem im selben Repository wie die Pull-Anfrage befindet.

| Verknüpftes Problem | Syntax | Beispiel |
| --- | --- | --- |
| Ausgabe im selben Repository | _SCHLÜSSELWORT_ # AUSGABE _\-NUMMER_ | `Closes #10` |
| Ausgabe in einem anderen Repository | _KEYWORD_ _OWNER_ / _REPOSITORY_ # _ISSUE-NUMBER_ | `Fixes octo-org/octo-repo#100` |
| Mehrere Probleme | Verwenden Sie für jedes Problem die vollständige Syntax | `Resolves #10, resolves #123, resolves octo-org/octo-repo#100` |

Nur manuell verknüpfte Pull-Requests können manuell entkoppelt werden. Um die Verknüpfung eines Problems aufzuheben, das Sie mit einem Schlüsselwort verknüpft haben, müssen Sie die Pull-Request-Beschreibung bearbeiten, um das Schlüsselwort zu entfernen.

Sie können auch schließende Schlüsselwörter in einer Commit-Nachricht verwenden. Das Problem wird geschlossen, wenn Sie den Commit in den Standard-Branch zusammenführen, aber die Pull-Anforderung, die den Commit enthält, wird nicht als verknüpfte Pull-Anforderung aufgeführt.

Jeder mit Schreibberechtigungen für ein Repository kann eine Pull-Anforderung manuell mit einem Vorgang über die Seitenleiste für Pull-Anforderungen verknüpfen.

Sie können bis zu zehn Issues manuell mit jeder Pull-Anfrage verknüpfen. Das Issue und die Pull-Anforderung müssen sich im selben Repository befinden.

1.  Navigieren Sie auf GitHub.com zur Hauptseite des Repositorys.
    
2.  Klicken Sie unter Ihrem Repository-Namen auf **Pull-Anforderungen** .
    
    ![Auswahl der Registerkarte „Probleme und Pull-Requests“.](https://docs.github.com/assets/cb-24580/images/help/repository/repo-tabs-pull-requests.png)
    
3.  Klicken Sie in der Liste der Pull-Requests auf den Pull-Request, den Sie mit einem Issue verknüpfen möchten.
    
4.  Klicken Sie in der rechten Seitenleiste im Abschnitt "Entwicklung" auf .
    
5.  Klicken Sie auf das Problem, das Sie mit der Pull-Anforderung verknüpfen möchten. ![Drop-down zum Link-Problem](https://docs.github.com/assets/cb-20278/images/help/pull_requests/link-issue-drop-down.png)
    

Jeder mit Schreibberechtigungen für ein Repository kann eine Pull-Anfrage manuell verknüpfen oder von der Issue-Seitenleiste zu einem Issue verzweigen.

Sie können bis zu zehn Issues manuell mit jeder Pull-Anfrage verknüpfen. Das Problem kann sich in einem anderen Repository befinden als der verknüpfte Pull-Request oder Branch. Ihr zuletzt ausgewähltes Repository wird gespeichert

1.  Navigieren Sie auf GitHub.com zur Hauptseite des Repositorys.
    
2.  Klicken Sie unter Ihrem Repository-Namen auf **Issues** .
    
    ![Registerkarte "Probleme".](https://docs.github.com/assets/cb-25896/images/help/repository/repo-tabs-issues.png)
    
3.  Klicken Sie in der Liste der Issues auf das Issue, mit dem Sie eine Pull-Anfrage oder einen Branch verknüpfen möchten.
    
4.  Klicken Sie in der rechten Seitenleiste auf **Entwicklung** . ![Entwicklungsmenü in der rechten Seitenleiste](https://docs.github.com/assets/cb-37343/images/help/issues/development-menu.png)
    
5.  Klicken Sie auf das Repository mit der Pull-Anfrage oder dem Zweig, den Sie mit dem Problem verknüpfen möchten. ![Drop-down, um das Repository auszuwählen](https://docs.github.com/assets/cb-109814/images/help/issues/development-menu-select-repository.png)
    
6.  Klicken Sie auf den Pull-Request oder Branch, den Sie mit dem Issue verknüpfen möchten. ![Drop-down, um Pull-Request oder Branch zu verknüpfen](https://docs.github.com/assets/cb-177162/images/help/issues/development-menu-select-pr-or-branch.png)
    
7.  Klicken Sie auf **Anwenden** . ![Anwenden](https://docs.github.com/assets/cb-165882/images/help/issues/development-menu-apply.png)
    

## [](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue#further-reading)Weiterlesen

-   " [Automatisch verlinkte Verweise und URLs](https://docs.github.com/en/articles/autolinked-references-and-urls/#issues-and-pull-requests) "
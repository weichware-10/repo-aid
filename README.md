# Weichware-10: Repo-Utils
Dieses Repository beinhaltet:
- [Workflows](workflows/),
- [.gitignore](.gitignore),
- [Checkstyle](checkstyle.xml)

welche alle in den folgenden Java-Repositories benötigt werden:
- [weichware10/toolbox](https://github.com/weichware10/toolbox)
- [weichware10/analyse](https://github.com/weichware10/analyse)
- [weichware10/util](https://github.com/weichware10/util)

und dort auch den gleichen Stand haben sollten.

---

## Checkstyle
siehe Dokumentation [hier](checkstyle.md)

---

## Workflows

### Update
Der [update](.github/workflows/update.yaml)-Workflow in diesem Repository sendet die Information über das Update an die anderen Repositories, welche das Update mit ihrem [update](workflows/update.yaml)-Workflow entgegennehmen und dem main-Branch comitten.
![Activity-Diagramm update.yaml](diagrams/update.svg)

### Tests
Der [tests](workflows/tests.yaml)-Workflow wird bei Änderungen von Java- und XML-Dateien aufgerufen und führt die Tests mit `mvn test` durch. Die Ergebnisse der Tests sind dann in Pull Requests einsehbar. Pull Requests dürfen nur gemerged werden, wenn keine Fehler mehr auftreten. Der Workflow schlägt auch fehl, falls der Build fehlschlägt.
![Activity-Diagramm tests.yaml](diagrams/tests.svg)

### Checkstyle
Der [checkstyle](workflows/checkstyle.yaml)-Workflow wird bei Änderungen von Java- und XML-Dateien aufgerufen und führt einen Stylecheck mit dem Maven-Checkstyle-Checkstyle Plugin durch. Eventuelle Probleme werden als Kommentar dem Pull Request beigefügt. Der Workflow schlägt fehl, falls es Style-Probleme gibt.  
Die Style-Regeln stammen aus [checkstyle.xml](checkstyle.xml) und werden [hier](checkstyle.md) dokumentiert.
Lokal kann man den Style mit `mvn verify checkstyle:check` oder mit der Checkstyle Erweiterung für VSCode checken.
![Activity-Diagramm checkstyle.yaml](diagrams/checkstyle.svg)

### Badges
Der [badges](workflows/badges.yaml)-Workflow wird bei Änderungen von Java-Dateien auf dem main-Branch aufgerufen und rendert svg-Dateien, welche den aktuellen Status der Tests und die Code Coverage anzeigen. Die Badges sind am Anfang der README-Dateien zu sehen.
![Activity-Diagramm badges.yaml](diagrams/badges.svg)

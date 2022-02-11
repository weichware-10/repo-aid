# Checkstyle Regeln

* Abgeleitet von [google_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml)

## Hinzugefügte Regeln
* Dateien sollten mit einem Zeilenumbruch aufhören.
    ```xml
    <module name="NewlineAtEndOfFile">
      <property name="fileExtensions" value="java, xml, yml"/>
    </module>
    ```
* Zeilen sollten nicht mehr Leerzeichen aufhören.
    ```xml
    <module name="RegexpSingleline">
      <property name="format" value="\s+$" />
      <property name="message" value="Line has trailing whitespaces." />
    </module>
    ```
* Regeln können übersprungen werden. (Dies sollte jedoch möglichst nicht benutzt werden)
    ```xml
    <module name="SuppressWithPlainTextCommentFilter"/>
    ```
* Der Paramtername und die Beschreibung des Parameters in JavaDocs sollten von einem Bindestrich getrennt werden.
    ```xml
    <module name="Regexp">
      <property name="format" value="(@param [a-z][a-zA-Z0-9]*)( ++-\S|\S- |\S-\S| ++[^-])"/>
      <property name="illegalPattern" value="true"/>
      <property name="message" value="The parameter name and description are not seperated by &quot; - &quot;" />
    </module>
    ```

## sonstige Änderungen
* Hinzufügen von Erklärungen der RegExp für Variablenbenennung, zum Beispiel:
    ```diff
      <module name="MemberName">
        <property name="format" value="^[a-z][a-z0-9][a-zA-Z0-9]*$" />
    -   <message key="name.invalidPattern" value="Member name ''{0}'' must match pattern ''{1}''." />
    +   <message key="name.invalidPattern" value="Member name ''{0}'' must match pattern ''{1}'' (camelCase, start with lowercase, only alphanumerical)." />
      </module>
    ```

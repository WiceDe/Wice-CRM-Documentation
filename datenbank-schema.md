# Datenbank-Schema
In dieser Anleitung wird das Schema der Wice-CRM-Datenbank erklärt

## Inhaltsverzeichnis
- [Tabellen](#tabellen)
  * [address_contactperson](#address-contactperson)
  * [address_company](#address-company)
  * [address_employee](#address-employee)
  * [ticket](#ticket)
  * [ticket_status](#ticket-status)
  * [ticket_type](#ticket-type)
  * [note](#note)
  * [chance](#chance)
  * [article](#article)
  * [category](#category)

## Tabellen
Dieser Abschnitt beinhaltet Informationen über ausgewählte Tabellen und erklärt deren Zweck und Felder. Bestimmte Felder sind dabei nur für interne Funktionen relevant und werden ggf. nicht aufgelistet.

### address_contactperson
In der Tabelle `address_contactperson` werden Informationen über in Wice gespeicherte Personen abgelegt.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID der Person.
- mandant: Beschreibt, unter welchem Wice-Mandanten diese Person gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- for_rowid: Falls diese Person zu einer Organisation zugeordnet ist, wird diese Organisation hier über deren rowid in der Tabelle `address_company` referenziert
- firstname: Vorname der Person
- name: Nachname der Person
- department: Abteilung
- position: Stelle/Position
- email: Email-Addresse
- phone: Telefonnummer
- phone2: Zusätzliche Telefonnummer
- phone3: Zusätzliche Telefonnummer
- mobile_phone: Mobilfunknummer
- private_email: Private Email-Addresse
- private_phone: Private Telefonnummer
- private_mobile_phone: Private Mobilfunknummer
- fax: Faxnummer
- xing_url: Link zum Xing-Profil
- facebook_url: Link zum Facebook-Profil
- linkedin_url: Link zum LinkedIn-Profil
- twitter_url: Link zum Twitter-Profil
- address_category_1: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_2: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_3: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_4: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- birthday: Datum des Geburtstags, formatiert als YYYY-MM-DD
- salutation: Titel bzw. Anschrift der Person, z.B. "Herr", "Frau", oder "Dr"
- serial_salutation: Briefanschrift der Person, z.B. "Sehr geehrte Frau Mustermann"
- private_country: Land der privaten Anschrift
- private_country_symbol: Kürzel des Landes der privaten Anschrift, z.b. "DE" oder "EN"
- private_zip_code: Postleitzahl der privaten Anschrift
- private_town: Stadt der privaten Anschrift
- private_street: Straße der privaten Anschrift
- private_street_number: Hausnummer der privaten Anschrift

### address_company
In der Tabelle `address_company` werden Informationen über in Wice gespeicherte Organisationen abgelegt.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID der Organisation.
- mandant: Beschreibt, unter welchem welchem Wice-Mandanten diese Organisation gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- name: Name der Organisation
- number_of_employees: Anzahl der Angestellten der Organisation
- turnover: Jährlicher Umsatz der Organisation
- remarks: Eingetragene Notizen über die Organisation
- url: Internet-Addresse der Homepage der Organisation
- email: Email-Addresse
- phone: Telefonnummer
- fax: Faxnummer
- xing_url: Link zum Xing-Profil
- facebook_url: Link zum Facebook-Profil
- linkedin_url: Link zum LinkedIn-Profil
- twitter_url: Link zum Twitter-Profil
- address_category_1: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_2: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_3: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_4: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- country: Land der Anschrift
- country_symbol: Kürzel des Landes der Anschrift, z.b. "DE" oder "EN"
- zip_code: Postleitzahl der Anschrift
- town: Stadt der Anschrift
- street: Straße der Anschrift
- street_number: Hausnummer der Anschrift

### address_employee
In der Tabelle `address_employee` werden Daten über die in Wice registrierten Mitarbeiter abgelegt. 

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten dieser Mitarbeiter gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- firstname: Vorname des Mitarbeiters
- name: Nachname des Mitarbeiters
- deactivated: Indiziert, ob dieser Mitarbeiter deaktiviert wurde. `1` steht für einen deaktivierten Mitarbeiter, `0` für einen nicht deaktivierten.
- birthday: Datum des Geburtstags, formatiert als YYYY-MM-DD
- department: Abteilung
- position: Stelle/Position
- email: Email-Addresse
- phone: Telefonnummer
- privphone: Private Telefonnummer
- fax: Faxnummer
- mobile_phone: Mobilfunknummer

### ticket
In der Tabelle `ticket` werden Informationen über in Wice gespeicherte Vorgänge abgelegt. Wichtig: Einzelne Einträge innerhalb eines Vorgangs sind in der Tabelle `note` zu finden.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID der Organisation.
- mandant: Beschreibt, unter welchem welchem Wice-Mandanten dieser Vorgang gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- subject: Initialer Betreff des Vorgangs
- date: Datum, an welchem der Vorgang erstellt wurde, formatiert als YYYY-MM-DD
- ticket_closed_on_date: Datum, an welchem der Vorgang ggf. abgeschlossen wurde, formatiert als YYYY-MM-DD
- for_rowid: Referenziert die zum Vorgang zugehörige Organisation über deren rowid in der Tabelle `address_company`
- employee_assigned: Referenziert den zugeordneten Mitarbeiter über dessen rowid in der Tabelle `address_employee`
- ticket_type: Art des tickets, referenziert über die rowid in der Tabelle `ticket_type`
- priority: Die Priorität des Vorgangs, ausgedrückt als ganze Zahl zwischen 1 und 5
- in_progress: Indiziert, ob der Vorgang momentan aktiv ist. `1` steht für einen aktiven Status, `0` oder `null` für einen inaktiven
- status: Der aktuelle Status des Vorgangs, referenziert über dessen rowid in der Tabelle `ticket_status`
- status_executed: Alle Status, die der Vorgang bisher durchlaufen hat. Formatiert als Reihe der jeweiligen rowids in chronologischer Reihenfolge von links nach rechts mit dem Separator `|`, z.B. `|185||186||192|`
- category_1: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_2: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_3: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_4: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`

### ticket_status

### ticket_type

### note

### chance

### article

### category

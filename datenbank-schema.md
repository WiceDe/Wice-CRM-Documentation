# Datenbank-Schema
In dieser Anleitung wird das Schema der Wice-CRM-Datenbank erklärt

## Tabellen
Dieser Abschnitt beinhaltet Informationen über ausgewählte Tabellen und erklärt deren Zweck und Felder. Bestimmte Felder sind dabei nur für interne Funktionen relevant und werden ggf. nicht aufgelistet.

### address_contactperson
In der Tabelle `address_contactperson` werden Informationen über in Wice gespeicherte Personen abgelegt.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID der Person.
- mandant: Beschreibt, unter welchem Mandant (referenziert als numerische ID) diese Person gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
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
- email: Private Email-Addresse
- phone: Private Telefonnummer
- mobile_phone: Private Mobilfunknummer
- fax: Faxnummer
- xing_url: Link zum Xing-Profil
- facebook_url: Link zum Facebook-Profil
- twitter_url: Link zum Twitter-Profil
- address_category_1: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_2: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_3: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- address_category_4: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- birthday: Datum des Geburtstags, formatiert als YYYY-MM-DD
- salutation: Titel bzw. Anschrift der Person, z.B. "Herr", "Frau", oder "Dr"
- serial_salutation: Briefanschrift der Person, z.B. "Sehr geehrte Frau Mustermann"

### address_company

### ticket

### note

### ticket_status

### chance

### article

### category

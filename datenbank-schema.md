# Datenbank-Schema
In dieser Anleitung wird das Schema der Wice-CRM-Datenbank erklärt

## Inhaltsverzeichnis
- [Tabellen](#tabellen)
  * [address_contactperson](#address-contactperson)
  * [address_company](#address-company)
  * [ticket](#ticket)
  * [note](#note)
  * [ticket_status](#ticket-status)
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

### ticket

### note

### ticket_status

### chance

### article

### category

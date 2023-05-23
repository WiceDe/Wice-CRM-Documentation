# Datenbank-Schema
In dieser Anleitung wird das Schema der Wice-CRM-Datenbank erklärt

## Inhaltsverzeichnis
- [Tabellen](#tabellen)
  * [address_contactperson](#address_contactperson)
  * [address_company](#address_company)
  * [address_employee](#address_employee)
  * [ticket](#ticket)
  * [ticket_status](#ticket_status)
  * [ticket_type](#ticket_type)
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
- birthday: Datum des Geburtstags, formatiert als `YYYY-MM-DD`
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
In der Tabelle `address_employee` werden Daten über die in Wice registrierten Mitarbeiter abgelegt. Auf diese wird u.A. von Vorgängen in der Tabelle `ticket` aus verwiesen

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten dieser Mitarbeiter gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- firstname: Vorname des Mitarbeiters
- name: Nachname des Mitarbeiters
- deactivated: Indiziert, ob dieser Mitarbeiter deaktiviert wurde. `1` steht für einen deaktivierten Mitarbeiter, `0` für einen nicht deaktivierten.
- birthday: Datum des Geburtstags, formatiert als `YYYY-MM-DD`
- department: Abteilung
- position: Stelle/Position
- email: Email-Addresse
- phone: Telefonnummer
- privphone: Private Telefonnummer
- fax: Faxnummer
- mobile_phone: Mobilfunknummer

### ticket
In der Tabelle `ticket` werden Informationen über in Wice gespeicherte Vorgänge abgelegt. Jede Zeile beschreibt genau einen Vorgang. Wichtig: Einzelne Einträge innerhalb eines Vorgangs sind in der Tabelle `note` zu finden.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID der Organisation.
- mandant: Beschreibt, unter welchem welchem Wice-Mandanten dieser Vorgang gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- subject: Initialer Betreff des Vorgangs
- date: Datum, an welchem der Vorgang erstellt wurde, formatiert als `YYYY-MM-DD
- ticket_closed_on_date: Datum, an welchem der Vorgang ggf. abgeschlossen wurde, formatiert als `YYYY-MM-DD`
- for_rowid: Referenziert die zum Vorgang zugehörige Organisation über deren rowid in der Tabelle `address_company`
- employee_assigned: Referenziert den zugeordneten Mitarbeiter über dessen rowid in der Tabelle `address_employee`
- ticket_type: Art des tickets, referenziert über die rowid in der Tabelle `ticket_type`
- priority: Die Priorität des Vorgangs, ausgedrückt als ganze Zahl zwischen 1 und 10
- in_progress: Indiziert, ob der Vorgang momentan aktiv ist. `1` steht für einen aktiven Status, `0` oder `null` für einen inaktiven
- status: Der aktuelle Status des Vorgangs, referenziert über dessen rowid in der Tabelle `ticket_status`
- status_executed: Alle Status, die der Vorgang bisher durchlaufen hat. Formatiert als Reihe der jeweiligen rowids in chronologischer Reihenfolge von links nach rechts mit dem Separator `|`, z.B. `|185||186||192|`
- category_1: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_2: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_3: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`
- category_4: Zugeordnete Kategorie, referenziert über die rowid in der Tabelle `category`

### ticket_status
In der Tabelle `ticket_status` werden die vom Nutzer definierten möglichen Status der Vorgänge abgelegt. Auf diese werden auf von der Tabelle `ticket` aus verwiesen.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten dieser Status gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- title: Titel bzw. Name des Status
- color: Farbe des Status in der Anzeige, im hexadezimalen RGB-Format, z.B. `d3d3d3` für Hellgrau

### ticket_type
In der Tabelle `ticket_type` werden die vom Nutzer definierten möglichen Arten von Vorgängen abgelegt. Auf diese werden von der Tabelle `ticket` aus verwiesen

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten dieser Ticket-Typ gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- title: Titel bzw. Name des Vorgangs-Typen
- ticket_status: Die möglichen Status, die von Vorgängen dieses Typen eingenommen werden können

### note
In der Tabelle `note` werden alle Einträge innerhalb von Vorgängen abgelegt. Jeder Eintrag bezieht auf genau einen Vorgang, und es kann beliebig viele Einträge pro Vorgang geben. Hier finden sich auch automatisierte Einträge, z.B. wenn der Status eines Vorgangs geändert wurde.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten dieser Eintrag gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- ticket: Referenziert den zugehörigen Vorgang über dessen rowid in der Tabelle `ticket`
- text: Inhalt des Eintrags
- employee_assigned: Referenziert den zugeordneten Mitarbeiter über dessen rowid in der Tabelle `address_employee`
- notify: Gesetzt, wenn ein weiterer Mitarbeiter über diese Notiz benachrichtigt wurde. Referenziert diesen über dessen rowid in der Tabelle `address_employee`
- is_reply_to: Gesetzt, wenn diese Eintrag eine Antwort auf einen anderen Eintrag ist. Referenziert diesen über dessen rowid in der Tabelle `note`
- contactperson: Referenziert die zugehörige Kontaktperson über deren rowid in der Tabelle `address_contactperson`
- priority: Eingetragene Priorität, formatiert als ganze Zahl zwischen 1 und 10
- last_update: Datum und Zeit, an dem der Eintrag erstellt wurde, formatiert als `YYYY-MM-DD hh-mm-ss`

### chance
In der Tabelle `chance` werden die eingetragenen Opportunities abgelegt.

#### Felder
- rowid: Eine in Wice eindeutige numerische ID des Mitarbeiters.
- mandant: Beschreibt, unter welchem Wice-Mandanten diese Opportunity gespeichert wurde. WICHTIG: Eine negative Zahl bedeutet, dass dieser Eintrag gelöscht wurde und sich im Papierkorb befindet
- description: Beschreibung der Opportunity
- article: Bezieht sich auf den Artikel, um den es sich in der Opportunity handelt. Referenziert diesen über dessen rowid in der Tabelle `article`
- articles_amount: Die Anzahl der Artikel in der Opportunity
- ticket: Referenziert den zugehörigen Vorgang über dessen rowid in der Tabelle `ticket
- salesman: Referenziert den zugeordneten Mitarbeiter über dessen rowid in der Tabelle `address_employee`
- probability: Vom Nutzer eingetragene geplante Wahrscheinlichkeit der Fakturierung in Prozent
- date: Datum, an dem die Opportunity eingetragen wurde, formatiert als `YYYY-MM-DD`
- planned_for_year: Das geplante Jahr, in dem die Opportunity fakturiert werden soll. Formatiert als `YYYY`
- planned_for_month: Der geplante Monat, in dem die Opportunity fakturiert werden soll. Formatiert als ganze Zahl zwischen 0 (Januar) und 11 (Dezember)
- actual_sales_date: Das Datum der Fakturierung der Opportunity, formatiert als `YYYY-MM-DD`. Standardwert `0000-00-00`, solange die Opportunity noch nicht fakturiert wurde
- sales_price: Der geplante Verkaufswert der Opportunity
- purchase_price: Die geplanten Einkaufskosten der Opportunity
- actual_sales_price: Der tatsächliche Verkaufswert der Opportunity nach Fakturierung. Standardwert `0`, solange die Opportunity noch nicht fakturiert wurde
- actual_purchase_price: Die tatsächlichen Einkaufskosten der Opportunity nach Fakturierung. Standardwert `0`, solange die Opportunity noch nicht fakturiert wurde
- discount_included_in_actual_sales_price: Rabatt der Fakturierung in Prozent, automatisch berechnet aus der Differenz des geplanten und tatsächlichen Verkaufswerts
- discount_text: Vom Nutzer eingetragener Hintergrund des Rabatts
- tax: Steuersatz der Opportunity in Prozent

### article

### category

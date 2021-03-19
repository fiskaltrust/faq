## Question

Where does fiskaltrust store which data?

## Question

Where is the POSArchive and AKO data stored in an audit-proof manner?

## Question

Where are the archived DSFinV-K and TSE TAR files located?

## Question

At which storage location is the data archived by fiskaltrust in an audit-proof manner?

## Metadata tags

lang-en, market-de, data-archive, bundle-carefree, PosCreator, PosDealer, PosOperator, Consultant

## Answer

### Type of data

Client-related data (= name, address, contact data, UID number, orders, etc. from cash register manufacturers, cash register dealers, cash register operators)
Configuration and status data (= TSE certificate, ClientId, status of the queue, etc.)
Mass data (= ReceiptRequest, ReceiptResponse)
Revision-secured client-related mass data (= .Tar-File, DSFinV-K-File, etc.)
General customer-related bulk data (= copy of everything that is manually stored in revision-secured customer-related bulk data, invoices, contracts, etc.)

### Processing locations

Azure Region West-Europe (a104, a105)
Azure-Region Germany-West-Central  (a110, a111)
Azure-Region France-Central (a107, a108)
Equinix-Datacenter Amsterdam (nl18) (https://www.equinix.com/locations/europe-colocation/netherlands-colocation/amsterdam-data-centers/)
RRZ-Datacenter Raaba / Graz (at11) (https://www.rrz.co.at/)

### Storage locations

SQL Azure West-Europe -> Mirror ( Azure North-Europe, Azure Germany-West-Central, Azure France-Central)
Dynamics365 EMEA Region (=crm4)
Massendaten Azure West-Europe -> Mirror Azure North-Europe
Kundenbezogene Massendaten Deutschland Azure Germany-West-Central

### Processing

General workloads are processed in West-Europe.
CPU-intensive workloads are processed in North-Europe and at11.
Customer-related data is managed exclusively in a separate Dynamics365 instance per country.
All services ending with "fiskaltrust.de" are processed with Azure Germany-West-Central (Microsoft Azure in Germany).
Customer-related mass data for configurations created with services ending in "fiskaltrust.de" are stored in Azure Germany-West-Central.
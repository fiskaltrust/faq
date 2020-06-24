## Question
Was ist ein Start-Beleg?

## Metadata tags
lang-at, lang-de, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Der _Start-Beleg_ muss als erster Beleg an den fiskaltrust.SecurityMechanism gesendet werden. Dadurch wird die entsprechende Queue initialisiert und alle weiteren Belege entsprechend den Gesetzen gesichert. Dieser Beleg erhält nur beim ersten Mal eine aussagekräftige Antwort vom fiskaltrust.SecurityMechanism, alle weiteren Start-Belege werden ignoriert und nicht beantwortet.

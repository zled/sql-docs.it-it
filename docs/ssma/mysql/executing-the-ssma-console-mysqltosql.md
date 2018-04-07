---
title: L'esecuzione la Console SSMA (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
caps.latest.revision: 25
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fb0022b9e4dd222fd3d19ed4dc3e6d03fc740bb
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="executing-the-ssma-console-mysqltosql"></a>L'esecuzione la Console SSMA (MySQLToSQL)
Microsoft fornisce un set affidabile di script di comandi di file per eseguire e controllare le attività SSMA.  
  
L'applicazione console utilizza alcuni comandi di file di script standard come enumerata in questa sezione.  
  
## <a name="project--script-file-commands"></a>Comandi di File di progetto Script  
**Command**  
  
create-new-project:   
                   Crea un nuovo progetto SSMA.  
  
I comandi di progetto di gestire la creazione di progetti, apertura, salvataggio e chiusura di progetti.  
  
**Script**  
  
1.  `project-folder` indica la cartella del progetto recupero creato.  
  
2.  `project-name` indica il nome del progetto. {string}  
  
3.  `overwrite-if-exists`Attributo facoltativo indica se è necessario sovrascrivere un progetto esistente. {booleano}  
  
4.  `project-type:`Attributo facoltativo. Indica il tipo di progetto, ad esempio "sql-server-2005" progetto o progetto "sql-server-2008" o "sql-server-2012" o "sql-server-2014" progetto o progetto "sql azure". Valore predefinito è "sql-server-2008".  
  
**Esempio di sintassi:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type==”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”   (optional)  
  
/>  
```  
Attributo 'sovrascrivere-if-exists' **false** per impostazione predefinita.  
  
Attributo 'tipo di progetto' **sql-server-2008** per impostazione predefinita.  
  
**Command**  
  
Apri progetto:   
                  Apre un progetto esistente.  
  
**Script**  
  
1.  `project-folder` indica la cartella del progetto recupero creato. Il comando non riesce se la cartella specificata non esiste.  {string}  
  
2.  `project-name` indica il nome del progetto. Il comando non riesce se il progetto specificato non esiste.  {string}  
  
**Esempio di sintassi:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> SSMA per applicazione Console MySQL supporta la compatibilità con le versioni precedenti. Sarà in grado di aprire progetti creati con la versione precedente di SSMA.  
  
**Command**  
  
progetto Salva: Salva il progetto di migrazione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
close-project  
                  : Consente di chiudere il progetto di migrazione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
close-project  
                  : Consente di chiudere il progetto di migrazione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Attributo 'if-modificata' è facoltativo, **ignorare** per impostazione predefinita.  
  
## <a name="database-connection-script-file-commands"></a>Comandi di File Script di database connessione  
I comandi di connessione al Database consentono di connettere al database.  
  
1.  Il **Sfoglia** funzionalità dell'interfaccia utente non è supportata nella console.  
  
2.  Il **l'autenticazione di windows** e **porta** parametri non sono applicabili quando ci si connette a SQL Azure.  
  
3.  Per ulteriori informazioni su 'Creazione di file di Script', vedere [creazione di file di Script &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
**Command**  
  
connect-source-database  
  
-   La connessione al database di origine e carica i metadati di livello elevato di database di origine, ma non tutti i metadati.  
  
-   Se non viene stabilita la connessione all'origine, viene generato un errore e l'applicazione console interrompe l'esecuzione  
  
**Script**  
  
Definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script.  
  
**Esempio di sintassi:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
force-load-source/target-database  
  
-   Carica i metadati di origine.  
  
-   È utile per l'utilizzo nel progetto di migrazione non in linea.  
  
-   Se non viene stabilita la connessione di origine/destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione  
  
**Script**  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```xml  
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
reconnect-source-database  
  
1.  Ristabilisce la connessione al database di origine, ma non carica i metadati a differenza del comando di connessione database di origine.  
  
2.  Se (ri) connessione con l'origine non viene stabilita, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
connect-target-database  
  
1.  Si connette al database di SQL Server o SQL Azure di destinazione e carica completamente elevato metadati a livello del database di destinazione, ma non nei metadati.  
  
2.  Se non viene stabilita la connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
Definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script  
  
**Esempio di sintassi:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
reconnect-target-database  
  
1.  Ristabilisce la connessione al database di destinazione, ma non carica i metadati, a differenza del comando di connessione database di destinazione.  
  
2.  Se non è possibile stabilire (ri) connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Comandi di File Script di report  
I comandi di Report generano report sulle prestazioni di varie attività della Console di SSMA.  
  
**Command**  
  
generate-assessment-report  
  
1.  Genera report di valutazione nel database di origine.  
  
2.  Se la connessione di database di origine non viene eseguita prima di eseguire questo comando, viene generato un errore e l'applicazione console viene chiusa.  
  
3.  Errore di connessione al server di database di origine durante l'esecuzione del comando, anche i risultati nell'applicazione console di terminazione.  
  
**Script**  
  
1.  `assessment-report-folder:` Specifica cartella in cui il report di valutazione può da archiviare. (attributo facoltativo)  
  
2.  `object-name:` Specifica gli oggetti considerati per la generazione di report di valutazione (può avere un nome di oggetto gruppo o nomi di oggetto singoli).  
  
3.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
4.  `assessment-report-overwrite:` Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
5.  `write-summary-report-to:` Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file con nome **AssessmentReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration--script-file-commands"></a>Comandi di File di Script di migrazione  
I comandi di migrazione convertire lo schema del database di destinazione per lo schema di origine e viene eseguita la migrazione di dati al server di destinazione.  
  
L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
**Command**  
  
convert-schema  
  
1.  Esegue la conversione dello schema di origine allo schema di destinazione.  
  
2.  Se la connessione di database di origine o di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di origine o di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
**Script**  
  
1.  `conversion-report-folder:` Specifica cartella in cui il report di valutazione può da archiviare. (attributo facoltativo)  
  
2.  `object-name:` Specifica gli oggetti considerati per la conversione dello schema (può avere un nome di oggetto gruppo o nomi di oggetto indivdual).  
  
3.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
4.  `conversion-report-overwrite:` Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
5.  `write-summary-report-to:` Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file con nome **SchemaConversionReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report di riepilogo ha due ulteriori sottocategorie:  
  
    -   `report-errors` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
migrate-data  
  
1.  Esegue la migrazione di dati di origine alla destinazione.  
  
**Script**  
  
1.  `object-name:` Specifica gli oggetti origine presi in considerazione per la migrazione dei dati (può avere un nome di oggetto gruppo o nomi di oggetto indivdual).  
  
2.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
3.  `write-summary-report-to:` Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file con nome **DataMigrationReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose` (= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true">  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <data-migration-connection  
  
         source-use-last-used="true"/source-server="<server-unique-name>"  
  
         target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
o  
  
```xml  
<migrate-data  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>Comando File Script di preparazione della migrazione  
Il comando di preparazione di migrazione avvia il mapping dello schema tra i database di origine e di destinazione.  
  
**Command**  
  
map-schema  
  
Mapping dello schema del database di origine allo schema di destinazione.  
  
**Script**  
  
1.  `source-schema` Specifica lo schema di origine che si intende eseguire la migrazione.  
  
2.  `sql-server-schema` Specifica lo schema di destinazione desiderata per la migrazione.  
  
**Esempio di sintassi:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Comandi di File di Script di gestibilità  
I comandi di gestione consentono di sincronizzare gli oggetti di database di destinazione con il database di origine.  
  
> [!NOTE]  
> L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
**Command**  
  
synchronize-target  
  
1.  Sincronizza gli oggetti di destinazione con il database di destinazione.  
  
2.  Se questo comando viene eseguito sul database di origine, si verifica un errore.  
  
3.  Se la connessione di database di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
**Script**  
  
1.  `object-name:` Specifica gli oggetti considerati per la sincronizzazione con database di destinazione (può avere un nome di oggetto gruppo o nomi di oggetto indivdual).  
  
2.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
3.  `on-error:` Specifica se specificare gli errori di sincronizzazione come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
4.  `report-errors-to:` Specifica percorso di segnalazione errori per l'operazione di sincronizzazione (attributo facoltativo) se il percorso di cartella viene fornito solo, quindi di file in base al nome **TargetSynchronizationReport.XML** viene creato.  
  
**Esempio di sintassi:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
o  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
o  
  
```xml  
<synchronize-target>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
**Command**  
  
aggiornamento da database  
  
1.  Aggiorna gli oggetti di origine dal database.  
  
2.  Se questo comando viene eseguito sul database di destinazione, viene generato un errore.  
  
**Script**  
  
1.  `object-name:` Specifica gli oggetti origine presi in considerazione per l'aggiornamento dal database di origine (può avere un nome di oggetto gruppo o nomi di oggetto indivdual).  
  
2.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
3.  `on-error:` Specifica se specificare gli errori di sincronizzazione come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
4.  `report-errors-to:` Specifica percorso di segnalazione errori per l'operazione di sincronizzazione (attributo facoltativo) se il percorso di cartella viene fornito solo, quindi di file in base al nome **SourceDBRefreshReport.XML** viene creato.  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
o  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
o  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Comandi File Script di generazione script  
I comandi di generazione dello Script eseguono due attività: consentono di salvare la console di output in un file di script. e registrare l'output di T-SQL nella console o un file in base al parametro specificato.  
  
**Command**  
  
come Save-script  
  
Consente di salvare gli script degli oggetti in un file indicato quando metabase = destinazione, si tratta di un'alternativa al comando di sincronizzazione in cui in si richiamare gli script e si esegue lo stesso nel database di destinazione.  
  
**Script**  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
1.  `object-name:` Specifica gli oggetti il cui script devono essere salvati. (Può avere un nome di oggetto gruppo o nomi di oggetto di indivdual)  
  
2.  `object-type:` Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se si specifica categoria dell'oggetto tipo di oggetto sarà "category").  
  
3.  `metabase:` Specifica se è l'origine o destinazione della metabase.  
  
4.  `destination:` Specifica il percorso o la cartella in cui lo script deve essere salvato, se il nome del file non è specificato quindi un nome di file in out il formato (valore dell'attributo object_name)  
  
5.  `overwrite:` Se true vengono sovrascritti se stesso nome di file esiste. Ciò può avere i valori (true/false).  
  
**Esempio di sintassi:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file-name/folder-name>”  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file-name/folder-name>”  
  
      <metabase-object object-name="<object-name>"  
  
            object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
convert-sql-statement  
  
1.  `context` Specifica il nome dello schema.  
  
2.  `destination` Specifica se l'output deve essere archiviata in un file.  
  
    Se questo attributo viene omesso, l'istruzione T-SQL convertito viene visualizzato nella console. (attributo facoltativo)  
  
3.  `conversion-report-folder` Specifica cartella in cui il report di valutazione può da archiviare. (attributo facoltativo)  
  
4.  `conversion-report-overwrite` Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
5.  `write-converted-sql-to` Specifica il percorso di cartella in cui è archiviato il codice T-SQL convertito file (o). Quando è specificato un percorso di cartella con il `sql-files` attributo, ogni file di origine sarà necessario una file di T-SQL creata nella cartella specificata di destinazione corrispondente. Quando è specificato un percorso di cartella con il `sql` attributo, il codice T-SQL convertito viene scritto in un file denominato Result.out sotto la cartella specificata.  
  
6.  `sql` Specifica le istruzioni sql MySQL da convertire, una o più istruzioni possono essere separati con un ";"  
  
7.  `sql-files` Specifica il percorso dei file sql che deve essere convertito in codice T-SQL.  
  
8.  `write-summary-report-to` Specifica il percorso in cui verrà generato il report di riepilogo. Se viene specificato il percorso della cartella, solo file in base al nome **ConvertSQLReport.XML** viene creato. (attributo facoltativo)  
  
    Report creazione è 2 ulteriormente mediante le sottocategorie..,:  
  
    -   report-errori (= "true/false" con valore predefinito è "false" (attributi facoltativi)).  
  
    -   verbose (= "true/false", con valore predefinito è "false" (attributi facoltativi)).  
  
**Script**  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
      <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
o  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
o  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Passaggio successivo  
Per informazioni sulle opzioni della riga di comando, vedere [opzioni della riga di comando nella Console di SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Per ulteriori informazioni sui file di script di esempio della console, vedere [funziona con i file di Script di esempio della Console &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Il passaggio successivo dipende dai requisiti del progetto:  
  
1.  Consente di specificare una password o l'esportazione / importazione per le password, vedere [la gestione delle password &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Per la generazione di report, vedere [la generazione di report &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Per la risoluzione dei problemi nella console, vedere [Troubleshooting &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  

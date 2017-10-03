---
title: L'esecuzione la Console SSMA (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 998a42b80fa415537051693467b337f07c9ba381
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="executing-the-ssma-console-sybasetosql"></a>L'esecuzione la Console SSMA (SybaseToSQL)
Microsoft fornisce un set affidabile di script di comandi di file per eseguire e controllare le attività SSMA. In dettaglio le sezioni che seguono lo stesso.  
  
## <a name="script-file-commands"></a>Comandi di file di script  
L'applicazione console utilizza alcuni comandi di file di script standard come enumerata in questa sezione.  
  
## <a name="project-commands"></a>Comandi di progetto  
I comandi di progetto di gestire la creazione di progetti, apertura, salvataggio e chiusura di progetti.  
  
### <a name="create-new-project"></a>creare-nuovo progetto  
Questo comando crea un nuovo progetto SSMA.  
  
-   `project-folder`indica la cartella del progetto recupero creato.  
  
-   `project-name`indica il nome del progetto. {stringa}  
  
-   `overwrite-if-exists`Attributo facoltativo indica se un progetto esistente deve essere sovrascritti. {booleano}  
  
-   `project-type:`Attributo facoltativo. Indica il tipo di progetto, il progetto "sql-server-2005" o "sql-server-2008" progetto o progetto "sql-server-2012" o "sql-server-2014" progetto o progetto "sql azure". Il valore predefinito è "sql server 2008."  
  
**Esempio di sintassi:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type=”<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>”  
/>  
```  
Attributo 'sovrascrivere-if-exists' **false** per impostazione predefinita.  
  
Attributo 'tipo di progetto' **sql-server-2008** per impostazione predefinita.  
  
### <a name="open-project"></a>Apri progetto  
Questo comando apre il progetto.

-   `project-folder`indica la cartella del progetto recupero creato. Il comando non riesce se la cartella specificata non esiste.  {stringa}  
  
-   `project-name`indica il nome del progetto. Il comando non riesce se il progetto specificato non esiste.  {stringa}  
  
**Esempio di sintassi:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA per l'applicazione Console di SAP ASE supporta la compatibilità con le versioni precedenti. È possibile usarlo per aprire i progetti creati con la versione precedente di SSMA.  
  
### <a name="save-project"></a>Salva progetto  
Questo comando Salva il progetto di migrazione.  
  
**Esempio di sintassi:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>Chiudi progetto  
Questo comando chiude il progetto di migrazione.  
  
**Esempio di sintassi:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Attributo 'if-modificata' è facoltativo, **ignorare** per impostazione predefinita.  
  
## <a name="database-connection-commands"></a>Comandi di connessione di database  
I comandi di connessione al Database consentono di connettere al database.  
  
> [!NOTE]  
> - Il **Sfoglia** funzionalità dell'interfaccia utente non è supportata nella console.  
> - Per ulteriori informazioni su 'Creazione di file di Script', vedere [creazione di file di Script &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>connessione database di origine  
Questo comando esegue una connessione al database di origine e carica i metadati di alto livello di database di origine, ma non tutti i metadati.
  
Se non viene stabilita la connessione all'origine, viene generato un errore e l'applicazione console interrompe l'esecuzione.
  
La definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script.  
  
**Esempio di sintassi:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Force-carico-/ destinazione del database di origine  
Il comando Carica i metadati di origine e risulta utile per l'utilizzo nel progetto di migrazione non in linea.  
  
Se non viene stabilita la connessione di origine/destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
Questo comando richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```xml  
<force-load metabase=”<source/target>” >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>ristabilire la connessione database di origine  
Questo comando ristabilisce la connessione al database di origine, ma non carica i metadati a differenza del comando di connessione database di origine.  
  
Se (ri) connessione con l'origine non viene stabilita, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>connessione database di destinazione  
Questo comando si connette al database di SQL Server di destinazione e carica i metadati di alto livello del database di destinazione ma non i metadati completamente.  
  
Se non viene stabilita la connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
La definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script.  
  
**Esempio di sintassi:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>ristabilire la connessione database di destinazione  
  
Questo comando ristabilisce la connessione al database di destinazione, ma non carica i metadati, a differenza del comando di connessione database di destinazione.  
  
Se non è possibile stabilire (ri) connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Comandi del report  
I comandi di Report generano report sulle prestazioni di varie attività della Console di SSMA.  
  
### <a name="generate-assessment-report"></a>generare report di valutazione  
  
Questo comando genera il report di valutazione nel database di origine.  
  
Se la connessione di database di origine non viene eseguita prima di eseguire questo comando, viene generato un errore e l'applicazione console viene chiusa.  
  
Errore di connessione al server di database di origine durante l'esecuzione del comando, anche i risultati nell'applicazione console di terminazione.  
  
-   `conversion-report-folder:`Specifica la cartella in cui può essere archiviata la relazione di valutazione. (attributo facoltativo)  
  
-   `object-name:`Specifica gli oggetti considerati per la generazione di report di valutazione (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto indicato nell'attributo nome di oggetto (se è specificato, categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `conversion-report-overwrite:`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-summary-report-to:`Specifica il percorso in cui verrà generato il report.  
  
    Se viene specificato il percorso della cartella, solo file in base al nome **AssessmentReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>”             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>Comandi di migrazione  
I comandi di migrazione convertire lo schema del database di destinazione per lo schema di origine e la migrazione dei dati al server di destinazione.  
  
### <a name="convert-schema"></a>Converti schema  
Questo comando esegue la conversione degli schemi di origine allo schema di destinazione.  
  
Se la connessione di database di origine o di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di origine o di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
-   `conversion-report-folder:`Specifica una cartella in cui è archiviato il report di valutazione. (attributo facoltativo)  
  
-   `object-name:`Specifica gli oggetti origine considerati per la conversione dello schema (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto indicato nell'attributo nome di oggetto (se è specificato, categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `conversion-report-overwrite:`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-summary-report-to:`Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file in base al nome **SchemaConversionReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
o  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>eseguire la migrazione di dati  
Questo comando esegue la migrazione di dati di origine alla destinazione.  
  
-   `object-name:`Specifica gli oggetti origine presi in considerazione per la migrazione di dati (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto indicato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `write-summary-report-to:`Specifica il percorso in cui verrà generato il report.  
  
    Se viene specificato il percorso della cartella, solo file in base al nome **DataMigrationReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
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
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>Comando di preparazione della migrazione  
Il comando di preparazione di migrazione avvia il mapping dello schema tra i database di origine e di destinazione.  
  
> [!NOTE]  
> L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
### <a name="map-schema"></a>schema di mapping  
Questo comando fornisce il mapping dello schema del database di origine allo schema di destinazione.  
  
-   `source-schema`Specifica lo schema di origine per eseguire la migrazione.  
  
-   `sql-server-schema`Specifica lo schema di destinazione a cui verrà eseguita la migrazione dello schema di origine.  
  
**Esempio di sintassi:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Comandi di gestibilità  
I comandi di gestione consentono di sincronizzare gli oggetti di database di destinazione con il database di origine.  
  
> [!NOTE]  
> L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
### <a name="synchronize-target"></a>sincronizzare-destinazione  
Questo comando consente di sincronizzare gli oggetti di destinazione con il database di destinazione.  
 
Se questo comando viene eseguito sul database di origine, si verifica un errore.  
  
Se la connessione di database di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
-   `object-name:`Specifica gli oggetti di destinazione, considerati per la sincronizzazione con database di destinazione (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto indicato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `on-error:`Specifica se specificare gli errori di sincronizzazione come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
-   `report-errors-to:`Specifica posizione del report di errore per l'operazione di sincronizzazione (attributo facoltativo). Se viene fornito il percorso di cartella, solo file in base al nome **TargetSynchronizationReport.XML** viene creato.  
  
**Esempio di sintassi:**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
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
  
### <a name="refresh-from-database"></a>aggiornamento da database  
Questo comando Aggiorna gli oggetti di origine dal database.  
  
Se questo comando viene eseguito sul database di destinazione, viene generato un errore.  
  
Questo comando richiede uno o più nodi di metabase come parametro della riga di comando.  
  
-   `object-name:`Specifica gli oggetti origine considerati per l'aggiornamento dal database di origine (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `on-error:`Specifica se chiamare aggiornamento errori come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
-   `report-errors-to:`Specifica posizione del report di errore per l'operazione di aggiornamento (attributo facoltativo). Se viene fornito il percorso di cartella, solo file in base al nome **SourceDBRefreshReport.XML** viene creato.  
  
**Esempio di sintassi:**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
o  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
o  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Comandi di generazione script  
I comandi di generazione dello Script eseguono due attività: consentono di salvare l'output in un file di script della console e registrano l'output di T-SQL nella console o un file in base al parametro specificato.  
  
### <a name="save-as-script"></a>come Save-script  
Questo comando viene utilizzato per salvare gli script degli oggetti in un file è indicato quando metabase = destinazione. Si tratta di un'alternativa al comando di sincronizzazione, in quanto si richiamare gli script e si esegue lo stesso nel database di destinazione.  
  
Questo comando richiede uno o più nodi di metabase come parametro della riga di comando.  
  
-   `object-name:`Specifica gli oggetti il cui script devono essere salvati (supporta i nomi di singolo oggetto o un nome di oggetto gruppo).  
  
-   `object-type:`Specifica il tipo dell'oggetto indicato nell'attributo nome di oggetto (se è specificato, categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `metabase:`Specifica se è l'origine o destinazione della metabase.  
  
-   `destination:`Specifica il percorso o la cartella in cui deve essere salvato lo script. Se non viene specificato il nome del file, verrà fornito un nome di file in out il formato (valore di attributo object_name).
  
-   `overwrite:`Se true, sovrascrive lo stesso nome file se esistente. Ciò può avere i valori (true/false).  
  
**Esempio di sintassi:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>Convert-istruzione
Questo comando Converte l'istruzione SQL.  
  
-   `context`Specifica il nome dello schema.  
  
-   `destination`Specifica se l'output deve essere archiviata in un file.  
  
    Se questo attributo viene omesso, l'istruzione T-SQL convertito viene visualizzato nella console. (attributo facoltativo)  
  
-   `conversion-report-folder`Specifica la cartella in cui può essere archiviata la relazione di valutazione. (attributo facoltativo)  
  
-   `conversion-report-overwrite`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-converted-sql-to`Specifica il percorso della cartella file (o) per cui devono essere archiviati convertito T-SQL. Quando è specificato un percorso di cartella con il `sql-files` , ogni file di origine e presenta una destinazione corrispondente file T-SQL creata nella cartella specificata. Quando è specificato un percorso di cartella con il `sql` attributo, il codice T-SQL convertito viene scritto in un file denominato Result.out sotto la cartella specificata.  
  
-   `sql`Specifica le istruzioni sql Sybase da convertire uno o più istruzioni possono essere separate con un ";"  
  
-   `sql-files`Specifica il percorso dei file sql che deve essere convertito in codice T-SQL.  
  
-   `write-summary-report-to`Specifica il percorso in cui verrà generato il report di riepilogo. Se viene specificato il percorso della cartella, solo file in base al nome **ConvertSQLReport.XML** viene creato. (attributo facoltativo)  
  
    Creazione di report di riepilogo ha due ulteriori sottocategorie, vale a dire:  
  
    -   report-errori (= "true/false" con valore predefinito è "false" (attributi facoltativi)).  
  
    -   verbose (= "true/false", con valore predefinito è "false" (attributi facoltativi)).  
  
Questo comando richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
o  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
o  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>Passaggi successivi  
Per informazioni sulle opzioni della riga di comando, vedere [opzioni della riga di comando della Console di SSMA (AccessToSQL)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Per informazioni su un file di script di esempio console, vedere [funziona con i file di Script di esempio Console &#40; SybaseToSQL &#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Il passaggio successivo dipende dai requisiti del progetto:  
  
-   Per specificare una password o l'esportazione / importazione per le password, vedere [le password di gestione &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Per la generazione di report, vedere [la generazione di report &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Per la risoluzione dei problemi nella console, vedere [Troubleshooting &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  


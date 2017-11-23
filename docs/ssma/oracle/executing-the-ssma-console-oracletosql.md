---
title: L'esecuzione la Console SSMA (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Oracle SSMA Console
- Script File Commands, Script Generation Commands,Manageability Commands
- Script File Commands,Project Commands
ms.assetid: 7228ccba-c69f-4b4c-8664-01a2750183c5
caps.latest.revision: "43"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 16f646303766e8e249e2bd76a336bc5c3ee59049
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="executing-the-ssma-console-oracletosql"></a>L'esecuzione la Console SSMA (OracleToSQL)
Microsoft fornisce un set affidabile di script di comandi di file per eseguire e controllare le attività SSMA. L'applicazione console utilizza alcuni comandi di file di script standard come enumerata in questa sezione.  
  
## <a name="project-script-file-commands"></a>Comandi di File di progetto Script  
I comandi di progetto di gestire la creazione di progetti, apertura, salvataggio e chiusura di progetti.  
  
**Command**  
  
creare-nuovo progetto  
                  : Crea un nuovo progetto SSMA.  
  
**Script**  
  
-   `project-folder`indica la cartella del progetto recupero creato.  
  
-   `project-name`indica il nome del progetto. {stringa}  
  
-   `overwrite-if-exists`Attributo facoltativo indica se un progetto esistente deve essere sovrascritti. {booleano}  
  
-   `project-type:`Attributo facoltativo. Indica il tipo di progetto, ovvero "sql-server-2005" progetto o progetto "sql-server-2008" o "sql-server-2012" progetto o il progetto "sql-server-2014" o "sql azure". Valore predefinito è "sql-server-2014".  
  
**Esempio:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014>"   (optional)  
  
/>  
```  
Attributo 'sovrascrivere-if-exists' **false** per impostazione predefinita.  
  
Attributo 'tipo di progetto' **sql-server-2008** per impostazione predefinita.  
  
**Command**  
  
Apri progetto: apre un progetto esistente.  
  
**Script**  
  
-   `project-folder`indica la cartella del progetto recupero creato. Il comando non riesce se la cartella specificata non esiste.  {stringa}  
  
-   `project-name`indica il nome del progetto. Il comando non riesce se il progetto specificato non esiste.  {stringa}  
  
**Esempio di sintassi:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
SSMA per l'applicazione Console Oracle supporta la compatibilità con le versioni precedenti. Sarà in grado di aprire progetti creati con la versione precedente di SSMA.  
  
**Command**  
  
Salva progetto  
  
Salva il progetto di migrazione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Chiudi progetto  
  
Chiude il progetto di migrazione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>Comandi di File Script di database connessione  
I comandi di connessione al Database consentono di connettere al database.  
  
-   Il **Sfoglia** funzionalità dell'interfaccia utente non è supportata nella console.  
  
-   Per ulteriori informazioni su 'Creazione di file di Script', vedere [OracleToSQL creazione di file di Script &#40; &#41;](../../ssma/oracle/creating-script-files-oracletosql.md).  
  
**Command**  
  
connessione database di origine  
  
-   La connessione al database di origine e carica i metadati di livello elevato di database di origine, ma non tutti i metadati.  
  
-   Se non viene stabilita la connessione all'origine, viene generato un errore e l'applicazione console interrompe l'esecuzione  
  
**Script**  
  
Definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script.  
  
**Esempio di sintassi:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Force-carico-/ destinazione del database di origine  
  
-   Carica i metadati di origine.  
  
-   È utile per l'utilizzo nel progetto di migrazione non in linea.  
  
-   Se non viene stabilita la connessione di origine/destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione  
  
**Script**  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
**Esempio di sintassi:**  
  
```xml  
<force-load object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
o  
  
```xml  
<force-load>  
  
   <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
ristabilire la connessione database di origine  
  
-   Ristabilisce la connessione al database di origine, ma non carica i metadati a differenza del comando di connessione database di origine.  
  
-   Se (ri) connessione con l'origine non viene stabilita, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
connessione database di destinazione  
  
-   Si connette al database di SQL Server di destinazione e carica completamente elevato metadati a livello del database di destinazione, ma non nei metadati.  
  
-   Se non viene stabilita la connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
Definizione del server viene recuperata dall'attributo del nome definito per ogni connessione nella sezione server di file di connessione del server o il file di script  
  
**Esempio di sintassi:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
ristabilire la connessione database di destinazione  
  
-   Ristabilisce la connessione al database di destinazione, ma non carica i metadati, a differenza del comando di connessione database di destinazione.  
  
-   Se non è possibile stabilire (ri) connessione alla destinazione, viene generato un errore e l'applicazione console interrompe l'esecuzione.  
  
**Script**  
  
**Esempio di sintassi:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file--commands"></a>Comandi di File Script di report  
I comandi di Report generano report sulle prestazioni di varie attività della Console di SSMA.  
  
**Command**  
  
generare report di valutazione  
  
-   Genera report di valutazione nel database di origine.  
  
-   Se la connessione di database di origine non viene eseguita prima di eseguire questo comando, viene generato un errore e l'applicazione console viene chiusa.  
  
-   Errore di connessione al server di database di origine durante l'esecuzione del comando, anche i risultati nell'applicazione console di terminazione.  
  
**Script**  
  
-   `conversion-report-folder:`Specifica una cartella in cui la relazione di valutazione può essere archiviati. (attributo facoltativo)  
  
-   `object-name:`Specifica gli oggetti considerati per la generazione di report di valutazione (può avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `conversion-report-overwrite:`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-summary-report-to:`Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file in base al nome **AssessmentReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   assessment-report-folder="<folder-name>"   (optional)  
  
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
  
## <a name="migration-script-file-commands"></a>Comandi di File di Script di migrazione  
I comandi di migrazione convertire lo schema del database di destinazione per lo schema di origine e viene eseguita la migrazione di dati al server di destinazione.  
  
L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
**Command**  
  
Converti schema  
  
-   Esegue la conversione dello schema di origine allo schema di destinazione.  
  
-   Se la connessione di database di origine o di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di origine o di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
**Script**  
  
-   `conversion-report-folder:`Specifica una cartella in cui la relazione di valutazione può essere archiviati. (attributo facoltativo)  
  
-   `object-name:`Specifica gli oggetti origine considerati per la conversione dello schema (può avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
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
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
eseguire la migrazione di dati  
  
Esegue la migrazione di dati di origine alla destinazione.  
  
**Script**  
  
-   `conversion-report-folder:`Specifica una cartella in cui la relazione di valutazione può essere archiviati. (attributo facoltativo)  
  
-   `object-name:`Specifica gli oggetti origine presi in considerazione per la migrazione di dati (può avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `conversion-report-overwrite:`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-summary-report-to:`Specifica il percorso in cui verrà generato il report di riepilogo.  
  
    Se viene specificato il percorso della cartella, solo file in base al nome **DataMigrationReport&lt;n&gt;. XML** viene creato. (attributo facoltativo)  
  
    Creazione di report presenta due ulteriori sottocategorie:  
  
    -   `report-errors`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
    -   `verbose`(= "true/false", con valore predefinito è "false" (attributi facoltativi))  
  
**Esempio di sintassi:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>">  
  
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
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Comandi di File Script di migrazione preparazione  
Il comando di preparazione di migrazione avvia il mapping dello schema tra i database di origine e di destinazione.  
  
**Command**  
  
schema di mapping  
  
Mapping dello schema del database di origine allo schema di destinazione.  
  
Esegue la migrazione di dati di origine alla destinazione.  
  
**Script**  
  
-   `source-schema`Specifica lo schema di origine che si intende eseguire la migrazione.  
  
-   `sql-server-schema`Specifica lo schema di destinazione in cui si desidera eseguire la migrazione.  
  
**Esempio di sintassi:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Comandi di File di Script di gestibilità  
I comandi di gestione consentono di sincronizzare gli oggetti di database di destinazione con il database di origine. L'output di console predefinito per i comandi di migrazione è il report di output 'Full' con Nessuna segnalazione di errore dettagliato: riepilogo solo dal nodo radice dell'albero di origine oggetto.  
  
**Command**  
  
sincronizzare-destinazione  
  
-   Sincronizza gli oggetti di destinazione con il database di destinazione.  
  
-   Se questo comando viene eseguito sul database di origine, si verifica un errore.  
  
-   Se la connessione di database di destinazione non viene eseguita prima di eseguire questo comando o la connessione al server di database di destinazione non riesce durante l'esecuzione del comando, viene generato un errore e l'applicazione console viene chiusa.  
  
**Script**  
  
-   `object-name:`Specifica gli oggetti di destinazione, considerati per la sincronizzazione con il database di destinazione (può avere un nome di oggetto gruppo o nomi di oggetto di indivdual).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `on-error:`Specifica se specificare gli errori di sincronizzazione come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
-   `report-errors-to:`Specifica posizione del report di errore per l'operazione di sincronizzazione (attributo facoltativo) se viene fornito il percorso di cartella, solo file in base al nome **TargetSynchronizationReport.XML** viene creato.  
  
**Esempio di sintassi:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
-   Aggiorna gli oggetti di origine dal database.  
  
-   Se questo comando viene eseguito sul database di destinazione, viene generato un errore.  
  
**Script**  
  
Richiede uno o più nodi di metabase come parametro della riga di comando.  
  
-   `object-name:`Specifica gli oggetti origine considerati per l'aggiornamento dal database di origine (può avere un nome di oggetto gruppo o nomi di oggetto singolo).  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `on-error:`Specifica se specificare gli errori di aggiornamento come avvisi o errori. Opzioni disponibili in errore:  
  
    -   Totale report come avviso  
  
    -   report-ogni-come-avviso  
  
    -   Errore-script  
  
-   `report-errors-to:`Specifica posizione del report di errore per l'operazione di aggiornamento (attributo facoltativo) se viene fornito il percorso di cartella, solo file in base al nome **SourceDBRefreshReport.XML** viene creato.  
  
**Esempio di sintassi:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
-   `object-name:`Specifica gli oggetti il cui script devono essere salvati. (Può avere un nome di oggetto gruppo o nomi di oggetto singoli)  
  
-   `object-type:`Specifica il tipo dell'oggetto specificato nell'attributo nome di oggetto (se è specificata una categoria dell'oggetto tipo di oggetto sarà "category").  
  
-   `metabase:`Specifica se è IIl origine o di destinazione della metabase.  
  
-   `destination:`Specifica il percorso o la cartella in cui lo script deve essere salvato, se il nome del file non è specificato quindi un nome di file in out il formato (valore di attributo object_name)  
  
-   `overwrite:`Se true vengono sovrascritti se lo stesso nome di file esiste. Ciò può avere i valori (true/false).  
  
**Esempio di sintassi:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file/folder>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
o  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
Convert-istruzione  
  
-   `context`Specifica il nome dello schema.  
  
-   `destination`Specifica se l'output deve essere archiviata in un file.  
  
    Se questo attributo viene omesso, l'istruzione T-SQL convertito viene visualizzato nella console. (attributo facoltativo)  
  
-   `conversion-report-folder`Specifica una cartella in cui la relazione di valutazione può essere archiviati. (attributo facoltativo)  
  
-   `conversion-report-overwrite`Specifica se sovrascrivere la cartella di report di valutazione se esiste già.  
  
    **Il valore predefinito:** false. (attributo facoltativo)  
  
-   `write-converted-sql-to`Specifica il percorso di cartella in cui è archiviato il codice T-SQL convertito file (o). Quando è specificato un percorso di cartella con il `sql-files` attributo, ogni file di origine sarà necessario una file di T-SQL creata nella cartella specificata di destinazione corrispondente. Quando è specificato un percorso di cartella con il `sql` attributo, il codice T-SQL convertito viene scritto in un file denominato **Result.out** sotto la cartella specificata.  
  
-   `sql`Specifica le istruzioni sql Oracle per la conversione, una o più istruzioni possono essere separati con un ";"  
  
-   `sql-files`Specifica il percorso dei file sql che deve essere convertito in codice T-SQL.  
  
-   `write-summary-report-to`Specifica il percorso in cui verrà generato il report. Se viene specificato il percorso della cartella, solo file in base al nome **ConvertSQLReport.XML** viene creato. (attributo facoltativo)  
  
    Report creazione è 2 ulteriormente le sottocategorie, dei quali.:  
  
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
  
   destination="<stdout/file>"   (optional)  
  
   file-name="<file-name>"  
  
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
  
   write-summary-report-to="<file-name/folder-name>" (optional)  
  
   verbose="<true/false>" (optional)  
  
   report-errors="<true/false>"  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
o  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>Passaggio successivo  
Per informazioni sulle opzioni della riga di comando, vedere [opzioni della riga di comando nella Console di SSMA &#40; OracleToSQL &#41;](../../ssma/oracle/command-line-options-in-ssma-console-oracletosql.md) .  
  
Per informazioni sui file di script di esempio console, vedere [funziona con i file di Script di esempio Console &#40; OracleToSQL &#41;](../../ssma/oracle/working-with-the-sample-console-script-files-oracletosql.md)  
  
Il passaggio successivo dipende dai requisiti del progetto:  
  
-   Per specificare una password o l'esportazione / importazione per le password, vedere [OracleToSQL le password di gestione &#40; &#41;](../../ssma/oracle/managing-passwords-oracletosql.md).  
  
-   Per la generazione di report, vedere [OracleToSQL la generazione di report &#40; &#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
-   Per la risoluzione dei problemi nella console, vedere [OracleToSQL Troubleshooting &#40; &#41;](../../ssma/oracle/troubleshooting-oracletosql.md).  
  

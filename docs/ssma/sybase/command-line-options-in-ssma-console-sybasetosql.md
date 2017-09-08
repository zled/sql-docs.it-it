---
title: Opzioni della riga di comando nella Console SSMA (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
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
- Sybase Console,Command Line Options
ms.assetid: 337cbd26-67b7-4c88-9deb-d0a69a3d7714
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f5dd6992056b19367f8e7f9d9ee4119976827764
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="command-line-options-in-ssma-console-sybasetosql"></a>Opzioni della riga di comando nella Console SSMA (SybaseToSQL)
Microsoft offre una serie di opzioni della riga di comando per eseguire e controllare le attività SSMA affidabili. In dettaglio le sezioni che seguono lo stesso.  
  
## <a name="command-line-options-in-ssma-console"></a>Opzioni della riga di comando nella Console SSMA  
Descritti nel presente documento è la console di opzioni di comando.  
  
In questa sezione, il termine 'option' è detta anche 'switch'.  
  
-   Opzioni non sono tra maiuscole e minuscole e può iniziare con '**-**'o',**/**' caratteri.  
  
-   Se sono state specificate, diventa obbligatorio per specificare i parametri di opzione corrispondente.  
  
-   I parametri di opzione devono essere separati dal carattere opzione da uno spazio vuoto.  
  
    **Esempi di sintassi:**  
  
    `C:\> SSMAforSybaseConsole.EXE -s scriptfile`  
  
    `C:\> SSMAforSybaseConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
-   I nomi di cartella o file contenenti spazi devono essere specificati tra virgolette doppie.  
  
-   L'output di voci di riga di comando e i messaggi di errore vengono archiviati in STDOUT o in un file specificato.  
  
### <a name="script-file-option-sscript"></a>Opzione di File di script: – s/script  
Un parametro obbligatorio, il percorso/nome del file script specifica lo script di sequenze di comando da eseguire tramite SSMA.  
  
**Esempi di sintassi:**  
  
`C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Opzione File valore variabile: variabile o – v  
Questo file include le variabili utilizzate nel file di script. Questo è un parametro facoltativo. Se le variabili non dichiarate nel file variabile e usate nel file di script, l'applicazione genera un errore e termina l'esecuzione della console.  
  
**Esempi di sintassi:**  
  
-   Variabili definite in più file di valore della variabile, ad esempio uno con un valore predefinito e un altro con un valore specifico dell'istanza quando applicabile. L'ultimo file di variabile specificato negli argomenti della riga di comando accetta la preferenza, in caso di una duplicazione delle variabili:  
  
    `C:\>SSMAforSybaseConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Opzione di File di connessione server: c: / serverconnection  
Questo file contiene informazioni sulla connessione di server per ogni server. Ogni definizione di server è identificato da un ID Server univoco. Gli ID del Server viene fatto riferimento nel file di script per la connessione comandi correlati.  
  
Definizione di server può essere una parte del file di connessione del server e/o file di script. Id del server nel file di script ha la precedenza sul file di connessione del server, in caso di una ripetizione dell'id del server.  
  
**Esempi di sintassi:**  
  
-   Gli ID dei server vengono utilizzati nel file di script e sono definiti in un file di connessione server separato, file di connessione del server utilizza le variabili definite nel file del valore della variabile:  
  
    `C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Definizione del server è incorporata nel file di script:  
  
    `C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Opzione di Output XML: - x / xmloutput [xmloutputfile]  
Questo comando viene utilizzato per i messaggi di output del comando in formato xml alla console o in un file xml di output.  
  
Sono disponibili due opzioni per xmloutput, dei quali..,:  
  
-   Se è specificato alcun percorso dopo il cambio di xmloutput l'output viene reindirizzato al file.  
  
    **Esempio di sintassi:**  
  
    `C:\>SSMAforSybaseConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Se non viene fornito alcun filepath dopo il cambio di xmloutput il xmlout viene visualizzato nella console di se stesso.  
  
    **Esempio di sintassi:**  
  
    `C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Opzione del File di log: – l o di log  
Tutte le operazioni di SSMA nell'applicazione Console ottengano registrate in un file di log. Questo è un parametro facoltativo. Se un file di log e il relativo percorso vengono specificati nella riga di comando, viene generato il log nel percorso specificato. In caso contrario, è generato dal percorso predefinito.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforSybaseConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Opzione di cartella di progetto ambiente: e: / projectenvironment  
Questo indica la cartella di impostazioni di ambiente di progetto per il progetto SSMA corrente. Questo parametro è facoltativo.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforSybaseConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option-psecurepassword"></a>Opzione Password sicura: – p/securepassword  
Questa opzione indica la password crittografata per le connessioni al server. Differisce da tutte le altre opzioni: l'opzione di qualsiasi script eseguito né consente di qualsiasi attività relative alla migrazione, ma consente di gestire la crittografia di password per le connessioni del server utilizzato nel progetto di migrazione.  
  
È possibile immettere qualsiasi altra opzione o la password come il parametro della riga di comando. In caso contrario, generato un errore. Per ulteriori informazioni, vedere il [la gestione delle password](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) sezione.  
  
Sono supportate le seguenti opzioni secondarie per `–p/securepassword`:  
  
-   Per aggiungere password protetta archiviazione per un ID di Server specificato o per tutti gli ID di Server definiti nel file di connessione del server. -Opzione per sovrascriverlo, seguito, gli aggiornamenti della password se esiste già:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Per rimuovere la password crittografata dalla risorsa di archiviazione protetta dell'ID del Server specificato o per tutti gli ID del Server:  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   Per visualizzare un elenco di ID di Server per cui la password viene crittografata:  
  
    `–p/securepassword –l/list`  
  
-   Per esportare le password archiviate in un archivio protetto a un file crittografato. Questo file è crittografato con la frase di sessione specificato dall'utente.  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   Il encrypted file esportato in precedenza viene importato in un percorso locale protetto utilizzando specificato dall'utente-passphrase. Una volta che il file viene decrittografato, archiviato in un nuovo file, a sua volta, verrà crittografato nel computer locale.  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    È possibile specificare più ID Server utilizzando separatori delle migliaia.  
  
### <a name="help-option-help"></a>Opzione della Guida:-? /help  
Visualizza il riepilogo della sintassi delle opzioni di SSMA Console:  
  
`C:\>SSMAforSybaseConsole.EXE -?`  
  
Per una visualizzazione tabulare delle opzioni della riga di comando SSMA Console, fare riferimento a [appendice - 1 &#40; SybaseToSQL &#41; ](../../ssma/sybase/appendix-1-sybasetosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>Opzione SecurePassword Help:: securepassword-? /Help  
Visualizza il riepilogo della sintassi delle opzioni di SSMA Console:  
  
`C:\>SSMAforSybaseConsole.EXE -securepassword -?`  
  
Per una visualizzazione tabulare delle opzioni della riga di comando SSMA Console, fare riferimento a [appendice - 1 &#40; SybaseToSQL &#41;](../../ssma/sybase/appendix-1-sybasetosql.md)  
  
### <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo dipende dai requisiti del progetto:  
  
-   Per specificare una password o l'esportazione / importazione per le password, vedere [le password di gestione &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Per la generazione di report, vedere [la generazione di report &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Per la risoluzione dei problemi nella console, vedere [Troubleshooting &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  


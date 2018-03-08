---
title: Opzioni della riga di comando nella Console SSMA (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
caps.latest.revision: "11"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: Inactive
ms.openlocfilehash: c1d26043b33ea902aec4ae7976ad8b215829bf34
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Opzioni della riga di comando della Console di SSMA (AccessToSQL)
Microsoft offre una serie di opzioni della riga di comando per eseguire e controllare le attività SSMA affidabili. Le sezioni che seguono forniscono dettagli aggiuntivi.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Opzioni della riga di comando nella Console di SSMA  
Descritti nel presente documento è la console di opzioni di comando.  
  
In questa sezione, il termine 'option' è detta anche 'switch'.  
  
Opzioni non sono tra maiuscole e minuscole e può iniziare con uno di '**-**'o'**/**' caratteri.  
  
Se sono state specificate, è obbligatorio specificare i parametri di opzione corrispondente.  
  
I parametri di opzione devono essere separati dal carattere opzione da uno spazio vuoto.  
  
**Esempi di sintassi:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
I nomi di cartella o file contenenti spazi devono essere specificati tra virgolette doppie.  
  
L'output dei messaggi di errore e le voci della riga di comando viene archiviato in STDOUT o in un file specificato.  
  
### <a name="script-file-option-sscript"></a>Opzione del file di script: – s/script  
Un parametro obbligatorio, il percorso/nome del file script specifica lo script di sequenze di comando da eseguire tramite SSMA.  
  
**Esempi di sintassi:**  
  
`C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Opzione del file di valore della variabile: la variabile o – v  
Il file con valori di variabile comprende le variabili utilizzate nel file di script. Il parametro è facoltativo. Se le variabili non dichiarate nel file variabile e usate nel file di script, l'applicazione genera un errore e termina l'esecuzione della console.  
  
**Esempi di sintassi:**  
  
-   Variabili definite in più file di valore della variabile, ad esempio uno con un valore predefinito e un altro con un valore specifico dell'istanza, se applicabile. L'ultimo file di variabile specificato negli argomenti della riga di comando accetta la preferenza, in caso di una duplicazione delle variabili:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Opzione file di connessione del server: / serverconnection-c  
Questo file contiene informazioni sulla connessione di server per ogni server. Ogni definizione di server è identificato da un ID Server univoco. Gli ID del Server viene fatto riferimento nel file di script per i comandi correlati alla connessione.  
  
Definizione di server può essere una parte del file di connessione del server e/o file di script. Id del server nel file di script ha la precedenza sul file di connessione del server, in caso di una ripetizione dell'id del server.  
  
**Esempi di sintassi:**  
  
-   Gli ID dei server vengono utilizzati nel file di script. Vengono definiti in un file di connessione server separato. Le variabili definite nel file del valore della variabile utilizzata dal file:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Definizione del server è incorporata nel file di script:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Opzione di output XML: - x / xmloutput [xmloutputfile]  
Questo comando viene utilizzato per i messaggi di output del comando in formato xml alla console o in un file xml di output.  
  
Sono disponibili due opzioni per xmloutput, vale a dire:  
  
-   Se il percorso di file non viene fornito dopo il cambio di xmloutput, l'output viene reindirizzato al file.  
  
    **Esempio di sintassi:**  
  
    `C:\>SSMAforAccessConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Se non viene fornito alcun filepath dopo il cambio di xmloutput, il xmlout viene visualizzato nella console di se stesso.  
  
    **Esempio di sintassi:**  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Opzione del file di log: – l o di log  
Tutte le operazioni di SSMA nell'applicazione Console vengono registrate in un file di log e il parametro è facoltativo. Se un file di log e il relativo percorso vengono specificati nella riga di comando, viene generato il log nel percorso specificato. In caso contrario, è generato dal percorso predefinito.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Opzione di ambiente cartella del progetto: e: / projectenvironment  
Questo parametro facoltativo indica la cartella di impostazioni di ambiente di progetto per il progetto SSMA corrente.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforAccessConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option-psecurepassword"></a>Proteggere l'opzione password: – p/securepassword  
Questa opzione indica la password crittografata per le connessioni al server. Differisce da tutte le altre opzioni, non eseguire qualsiasi script o della Guida in qualsiasi attività relative alla migrazione, ma consente di gestire la crittografia di password per le connessioni del server utilizzato nel progetto di migrazione.  
  
È possibile immettere qualsiasi altra opzione o la password come parametro della riga di comando. In caso contrario, generato un errore. Per ulteriori informazioni, vedere il [la gestione delle password](http://msdn.microsoft.com/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) sezione.  
  
Sono supportate le seguenti le opzioni secondarie per `–p/securepassword`:  
  
-   Per aggiungere una password o aggiornare una password esistente, per l'archiviazione protetta per un ID di Server specificato o per tutti gli ID di Server definiti nel file di connessione del server:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
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
  
### <a name="help-option-help"></a>Help (opzione):-? /help  
Visualizza il riepilogo della sintassi delle opzioni di SSMA Console:  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Per una visualizzazione tabulare di opzioni della riga di comando SSMA Console, fare riferimento a [appendice - 1 &#40; AccessToSQL &#41; ](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>Opzione della Guida SecurePassword:: securepassword-? /Help  
Visualizza il riepilogo della sintassi delle opzioni di SSMA Console:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Per una visualizzazione tabulare di opzioni della riga di comando SSMA Console, fare riferimento a [appendice - 1 &#40; AccessToSQL &#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo dipende dai requisiti del progetto:  
  
1.  Per specificare una password o l'esportazione / importazione per le password, vedere [le password di gestione &#40; AccessToSQL &#41; ](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Per la generazione di report, vedere [la generazione di report &#40; AccessToSQL &#41; ](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Per la risoluzione dei problemi nella console, vedere [Troubleshooting &#40; AccessToSQL &#41; ](../../ssma/access/troubleshooting-accesstosql.md).  
  

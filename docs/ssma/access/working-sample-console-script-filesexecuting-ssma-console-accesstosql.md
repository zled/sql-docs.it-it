---
title: Utilizzare la Console SSMA FilesExecuting Script di esempio Console | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ad75b648-d119-4119-98f0-d18f058be68d
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a2ac9806e1f7577312ede0dddfcd38b3721f94f0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="working-with-the-sample-console-script-filesexecuting-the-ssma-console-accesstosql"></a>Utilizzo di FilesExecuting Script Console di esempio la Console SSMA (AccessToSQL)
Alcuni file di esempio sono stati forniti insieme al prodotto per l'utilizzo e un riferimento all'utente. Questa sezione descrive il modo per personalizzare facilmente questi script per soddisfare le esigenze dell'utente finale.  
  
## <a name="sample-console-script-files"></a>File di Script di esempio Console  
I seguenti file script di esempio console relativi a diversi scenari sono stati forniti i riferimenti all'utente:  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   **ServersConnectionFileSample.xml:**  
  
    -   In questo esempio offre diverse modalità di connessione disponibili per il database di origine e di destinazione e l'utente può selezionare qualsiasi modalità in base al requisito. In questo esempio contiene le definizioni di Server.  
  
    -   L'utente può connettersi al database richiesto semplicemente modificando i valori all'origine richiesto e definizioni del server di destinazione. Nell'esempio fornito in tutti i valori sono stati forniti valori come variabili in cui sono disponibili nel **VariableValueFileSample.xml**. Tutti gli altri parametri di connessione possono essere rimosso dal file di connessione server di lavoro dell'utente.  
  
    -   Per ulteriori informazioni sulla connessione al server di origine e di destinazione, vedere [creare i file di connessione del Server &#40; AccessToSQL &#41; ](../../ssma/access/creating-the-server-connection-files-accesstosql.md) .  
  
-   **VariableValueFileSample.xml:** tutte le variabili che sono state usate nella console di esempio i file di script e `ServersConnectionFileSample.xml` sono stati confrontati in questo file. Per eseguire gli script di esempio console che l'utente deve sostituire semplicemente la variabile di esempio i valori con l'utente definito quelli e passare il file come argomento della riga di comando aggiuntivo oltre al file di script.  
  
    Per ulteriori informazioni sul File con valori variabili, vedere [creazione di file di valore variabile &#40; AccessToSQL &#41; ](../../ssma/access/creating-variable-value-files-accesstosql.md).  
  
-   **AssessmentReportGenerationSample.xml:** in questo esempio consente di generare un report di valutazione di xml che può essere utilizzato dall'utente per l'analisi cominciare convertire e la migrazione dei dati.  
  
    Nel `generate-assessment-report` comando l'utente deve obbligatoriamente includere modificare il valore della variabile (vedere **VariableValueFileSample.xml**) nel `object-name` attributo al nome di database da in uso dall'utente. A seconda del tipo dell'oggetto specificato, il `object-type` valore dovrà anche essere modificato.  
  
    Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `generate-assessment-report` di esempio 4 del comando del file di script della console di esempio.  
  
    Per ulteriori informazioni sulla generazione di report, vedere [la generazione di report &#40; AccessToSQL &#41; ](../../ssma/access/generating-reports-accesstosql.md).  
  
    > [!NOTE]  
    > -   Verificare che l'argomento della riga di comando file valore della variabile viene passata all'applicazione console e VariableValueFileSample.xml viene aggiornato con l'utente specificato i valori.  
    > -   Verificare che l'argomento della riga di comando server connessione file viene passato all'applicazione console e il ServersConnectionFileSample.xml viene aggiornata con i valori dei parametri server corretto.  
  
-   **ConversionAndDataMigrationSample.xml:** in questo esempio consente all'utente di eseguire una migrazione end-to-end dalla conversione per la migrazione dei dati. L'elenco dei valori di attributo obbligatorio che dovranno modificare elencata di seguito:  
  
    |Nome del comando|Description|Attribute|  
    |----------------|---------------|-------------|  
    |`map-schema`|Mapping dello schema del database di origine allo schema di destinazione.|`source-schema:`Specifica il database di origine che richiede da convertire.<br /><br />`sql-server-schema`: Specifica il database di destinazione che deve essere eseguita la migrazione a|  
    |`convert-schema`|Esegue la conversione dello schema di origine allo schema di destinazione.<br /><br />Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `convert-schema` di esempio 4 del comando del file di script della console di esempio.|`object-name`: Specificare il database di origine / nome che richiede la conversione dell'oggetto. Verificare che il corrispondente `object-type` viene modificato in base al tipo di oggetto specificato nel`object-name`|  
    |`synchronize-target`|Sincronizza gli oggetti di destinazione con il database di destinazione.<br /><br />Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `synchronize-target` di esempio 3 del comando del file di script della console di esempio.|`object-name:`Specificare il database di sql server / nome che richiede la creazione dell'oggetto. Verificare che il corrispondente `object-type` viene modificato in base al tipo di oggetto specificato nel`object-name`|  
    |`migrate-data`|Esegue la migrazione di dati di origine alla destinazione.<br /><br />Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `migrate-data` di esempio 2 del comando del file di script della console di esempio.|`object-name:`Specifica il database di origine / nome che è necessario eseguire la migrazione di tabelle. Verificare che il corrispondente `object-type` viene modificato in base al tipo di oggetto specificato nel`object-name`|  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di valore della variabile file &#40; AccessToSQL &#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
[Creare i file di connessione del Server &#40; AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
[Generazione di report &#40; AccessToSQL &#41;](../../ssma/access/generating-reports-accesstosql.md)  
  


---
title: Utilizzo dei file di Script di esempio Console (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Sample Console Script Files, ServersConnectionFileSample.xml
- Sample Console Script Files, SqlStatementConversionSample.xml
- Sample Console Script Files,VariableValueFileSample.xml
ms.assetid: c6202dcc-b994-457b-9b2f-0cd89e79792d
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: e1f95cff5d19282f32017786851d04a3d3322dc3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-the-sample-console-script-files-oracletosql"></a>Utilizzo dei file di Script di esempio Console (OracleToSQL)
Alcuni file di esempio sono stati forniti insieme al prodotto per l'utilizzo e un riferimento all'utente. Questa sezione descrive il modo per personalizzare facilmente questi script per soddisfare le esigenze dell'utente finale.  
  
## <a name="sample-console-script-files"></a>File di Script di esempio Console  
I seguenti file script di esempio console relativi a diversi scenari sono stati forniti i riferimenti all'utente:  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   **ServersConnectionFileSample.xml:**  
  
    -   In questo esempio offre diverse modalità di connessione disponibili per il database di origine e di destinazione e l'utente può selezionare qualsiasi modalità in base al requisito. In questo esempio contiene le definizioni di Server.  
  
    -   L'utente può connettersi al database richiesto semplicemente modificando i valori all'origine richiesto e definizioni del server di destinazione. Nell'esempio fornito in tutti i valori sono stati forniti valori come variabili in cui sono disponibili nel **VariableValueFileSample.xml**.  Tutti gli altri parametri di connessione possono essere rimosso dal file di connessione server di lavoro dell'utente.  
  
    -   Per ulteriori informazioni sulla connessione al server di origine e di destinazione, vedere [creano i file di connessione del Server &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md) .  
  
-   **VariableValueFileSample.xml:** tutte le variabili che sono state usate nella console di esempio i file di script e `ServersConnectionFileSample.xml` sono stati confrontati in questo file. Per eseguire gli script di esempio console che l'utente deve sostituire semplicemente la variabile di esempio i valori con l'utente definito quelli e passare il file come argomento della riga di comando aggiuntivo oltre al file di script.  
  
    Per ulteriori informazioni sul File con valori variabili, vedere [creazione di file di valore variabile &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md).  
  
-   **AssessmentReportGenerationSample.xml:** in questo esempio consente all'utente generare un report di valutazione xml che può essere usato dall'utente per l'analisi cominciare convertire e la migrazione dei dati.  
  
    Nel `generate-assessment-report` comando l'utente deve obbligatoriamente includere modificare il valore della variabile (vedere **VariableValueFileSample.xml**) nel `object-name` attributo al nome di database da in uso dall'utente. A seconda del tipo dell'oggetto specificato, il `object-type` valore dovrà anche essere modificato.  
  
    Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `generate-assessment-report` di esempio 4 del comando del file di script della console di esempio.  
  
    Per ulteriori informazioni sulla generazione di report, vedere [la generazione di report &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
    > [!NOTE]  
    > -   Verificare che l'argomento della riga di comando file valore della variabile viene passata all'applicazione console e VariableValueFileSample.xml viene aggiornato con l'utente specificato i valori.  
    > -   Verificare che l'argomento della riga di comando server connessione file viene passato all'applicazione console e il ServersConnectionFileSample.xml viene aggiornata con i valori dei parametri server corretto.  
  
-   **SqlStatementConversionSample.xml:**  
    In questo esempio consente di generare corrispondente `t-sql` script per il database di origine `sql` comando fornito come input.  
  
    Nel `convert-sql-statement` comando l'utente deve obbligatoriamente includere modificare il valore della variabile (vedere **VariableValueFileSample.xml**) nel `context` attributo al nome del database che viene utilizzato dall'utente. L'utente sarà inoltre necessario modificare il `sql` valore dell'attributo per il database di origine `sql` comando che potrà richiedere da convertire.  
  
    L'utente può anche fornire i file sql da convertire. Questa operazione è stata illustrata nel `convert-sql-statement` di esempio 4 del comando del file di script della console di esempio.  
  
    > [!NOTE]  
    > Verificare che l'argomento della riga di comando file valore della variabile viene passata all'applicazione console e VariableValueFileSample.xml viene aggiornato con l'utente specificato i valori.  
  
-   **ConversionAndDataMigrationSample.xml:**  
     In questo esempio consente all'utente di eseguire una migrazione end-to-end dalla conversione per la migrazione dei dati. L'elenco dei valori di attributo obbligatorio che dovranno modificare elencata di seguito:  
  
    **Nome del comando**  
  
    `map-schema`  
  
    Mapping dello schema del database di origine allo schema di destinazione.  
  
    **Attributo**  
  
    -   `source-schema:` Specifica il database di origine che richiede da convertire.  
  
    -   `sql-server-schema`: Specifica il database di destinazione che deve essere eseguita la migrazione a  
  
    **Nome del comando**  
  
    `convert-schema`  
  
    -   Esegue la conversione dello schema di origine allo schema di destinazione.  
  
    -   Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `convert-schema` di esempio 4 del comando del file di script della console di esempio.  
  
    **Attributo**  
  
    `object-name`: Specificare il database di origine / object name che richiede da convertire. Verificare che il corrispondente `object-type` viene modificato in base al tipo dell'oggetto specificato nella `object-name`  
  
    **Nome del comando**  
  
    `synchronize-target`  
  
    -   Sincronizza gli oggetti di destinazione con il database di destinazione.  
  
    -   Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `synchronize-target` di esempio 3 del comando del file di script della console di esempio.  
  
    **Attributo**  
  
    `object-name:` Specificare il database di sql server / nome che richiede la creazione dell'oggetto. Verificare che il corrispondente `object-type` viene modificato in base al tipo dell'oggetto specificato nella `object-name`  
  
    **Nome del comando**  
  
    `migrate-data`  
  
    -   Esegue la migrazione di dati di origine alla destinazione.  
  
    -   Se l'utente deve valutare più oggetti / database è possibile specificare più `metabase-object` nodi, come illustrato nel `migrate-data` di esempio 2 del comando del file di script della console di esempio.  
  
    **Attributo**  
  
    `object-name:` Specifica il database di origine / nome che è necessario eseguire la migrazione di tabelle. Verificare che il corrispondente `object-type` viene modificato in base al tipo dell'oggetto specificato nella `object-name`  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di file di valore della variabile &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
[La creazione dei file di connessione del Server &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
[Generazione di report &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md)  
  

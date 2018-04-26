---
title: Eseguire dalla riga di comando (SQL Server Data Migration Assistant) | Documenti Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: article
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bf0437354f90a03f1d1cf68be074df3f4234676
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Eseguire Data Migration Assistant dalla riga di comando
La versione 2.1 e versioni successive, quando si installa Data Migration Assistant, verranno installati anche dmacmd.exe in *% ProgramFiles %\\Microsoft Data Migration Assistant\\*. Utilizzare dmacmd.exe per valutare i database in modalità automatica e il risultato JSON o CSV file di output. Ciò è particolarmente utile quando si verifica più database o i database di grandi dimensioni. 

> [!NOTE]
> Dmacmd.exe supporta solo le valutazioni in esecuzione. In questo momento non sono supportate le migrazioni.


## <a name="command-line-arguments"></a>Argomenti della riga di comando

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```


|Argomento  |Description  | Obbligatorio (Y/N)
|---------|---------|---------------|
| `/help or /?`     | Come usare il testo della Guida dmacmd.exe        | N
|`/AssessmentName`     |   Nome del progetto di valutazione   | S
|`/AssessmentDatabases`     | Elenco delimitato da spazi delle stringhe di connessione. Nome del database (catalogo iniziale) è tra maiuscole e minuscole. | S
|`/AssessmentTargetPlatform`     | Piattaforma di destinazione per la valutazione, i valori supportati: SqlServer2012, SqlServer2014, SqlServer2016 e AzureSqlDatabaseV12. Il valore predefinito è SqlServer2016   | N
|`/AssessmentEvaluateFeatureParity`  | Eseguire le regole di parità di funzionalità  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Eseguire le regole di compatibilità  | S <br> (AssessmentEvaluateCompatibilityIssues o AssessmentEvaluateRecommendations è obbligatorio).
|`/AssessmentEvaluateRecommendations`     | Eseguire i suggerimenti di funzionalità        | S <br> (AssessmentEvaluateCompatibilityIssues o AssessmentEvaluateRecommendationsis richiesto)
|`/AssessmentOverwriteResult`     | Sovrascrivere il file dei risultati    | N
|`/AssessmentResultJson`     | Percorso completo del file di risultati JSON     | S <br> (È necessario AssessmentResultJson o AssessmentResultCsv)
|`/AssessmentResultCsv`    | Percorso completo del file di risultati CSV   | S <br>(È necessario AssessmentResultJson o AssessmentResultCsv)




## <a name="examples"></a>Esempi

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Valutazione di singolo database utilizzando le regole di compatibilità in esecuzione e l'autenticazione di Windows**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**Valutazione database singolo con suggerimento funzionalità di autenticazione e l'esecuzione di SQL Server**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**Valutazione di singolo database per la piattaforma di destinazione SQL Server 2012 e salvare i risultati in un file con estensione JSON e CSV**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```


**Valutazione di singolo database per la piattaforma di destinazione Database di SQL Azure salvare i risultati in file con estensione JSON e CSV**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```


**Valutazione di più database**

```
DmaCmd.exe /AssessmentName="TestAssessment"
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```



## <a name="see-also"></a>Vedere anche

[Download di Assistente per la migrazione dei dati](https://www.microsoft.com/download/details.aspx?id=53595)

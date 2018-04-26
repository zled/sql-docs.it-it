---
title: Le impostazioni di configurazione (SQL Server Data Migration Assistant) | Documenti Microsoft
ms.custom: ''
ms.date: 08/31/2017
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
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6fbe8b8a2912e7dfcc4b5f656255132e27e8a72
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configuration-settings-for-data-migration-assistant"></a>Impostazioni di configurazione per dati Migration Assistant

È possibile ottimizzare determinati comportamenti di dati Migration Assistant utilizzando i valori di configurazione nel file dma.exe.config. Questo articolo descrive i valori di chiave di configurazione.

È possibile trovare il file dma.exe.config per l'applicazione desktop di Assistente per la migrazione dei dati e l'utilità della riga di comando, nelle cartelle seguenti nel computer.

- Applicazione desktop

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dma.exe.config

- Utilità della riga di comando

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

Assicurarsi di salvare una copia del file di configurazione originale prima di apportare qualsiasi modifica. Dopo aver apportato modifiche, riavviare dati Migration Assistant per i nuovi valori di configurazione per rendere effettive.

## <a name="number-of-databases-to-assess-in-parallel"></a>Numero di database per valutare in parallelo

Dati della migrazione guidata consente di valutare più database in parallelo. Durante la valutazione dati Migration Assistant estrae applicazione livello dati (con estensione dacpac) per conoscere lo schema di database. Questa operazione può timeout se vengono valutati in parallelo in più database nello stesso server. 

A partire dalla versione 2.0 Data Migration Assistant, è possibile controllare questo impostando il parallelDatabases valore di configurazione. Valore predefinito è 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Numero di database per eseguire la migrazione in parallelo

Dati della migrazione guidata esegue la migrazione di più database in parallelo, prima che la migrazione degli account di accesso. Durante la migrazione, Data Migration Assistant verrà eseguire un backup del database di origine, se lo si desidera copiare il backup e quindi ripristinarlo nel server di destinazione. Quando sono selezionati più database per la migrazione, possono verificarsi errori di timeout. 

A partire dalla Data Migration Assistant v 2.0, se si verifica questo problema è possibile ridurre il valore di configurazione parallelDatabases. È possibile aumentare il valore per ridurre il tempo complessivo di migrazione.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases=”8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Impostazioni di DacFX

Durante la valutazione, dati Migration Assistant estrae applicazione livello dati (con estensione dacpac) per conoscere lo schema di database. Questa operazione può non riuscire con valori di timeout per il database molto grandi, o se il server è in condizioni di carico. A partire dalla versione 1.0 di migrazione dei dati, è possibile modificare i valori di configurazione seguente per evitare errori. 

> [!NOTE]
> L'intero &lt;dacfx&gt; voce è impostata come commento per impostazione predefinita. Rimuovere i commenti e quindi modificare il valore in base alle esigenze.

- CommandTimeout

   Impostare la proprietà IDbCommand.CommandTimeout in *secondi*. (Predefinito = 60)

- databaseLockTimeout

   Ciò equivale a [impostare blocco\_TIMEOUT timeout\_periodo ](../t-sql/statements/set-lock-timeout-transact-sql.md) in *millisecondi*. (Predefinito = 5000)

- maxDataReaderDegreeOfParallelism

   Numero di connessioni di pool di connessione SQL da utilizzare. (Predefinito = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```


## <a name="stretch-database-recommendation-threshold"></a>Estensione Database: Soglia di suggerimento

Con [estensione Database di SQL Server](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), consente di estendere in modo dinamico e sporadico dati transazionali da Microsoft SQL Server 2016 in Azure. Estensione Database destinazioni database transazionali che contengono grandi quantità di dati ad accesso sporadico. L'indicazione di estensione Database, nella raccomandazione di funzionalità di archiviazione, identifica innanzitutto le tabelle che ritiene che trarranno vantaggio da questa funzionalità, e quindi identifica le modifiche che devono essere apportate per abilitare la tabella per questa funzionalità.

A partire dalla versione 2.0 Data Migration Assistant, è possibile controllare questa soglia per una tabella per qualificarsi per la funzionalità estensione Database utilizzando il valore di configurazione recommendedNumberOfRows. Valore predefinito è 100.000 righe. Se si desidera analizzare le funzionalità di estensione per le tabelle anche più piccole, minore del valore di conseguenza.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Timeout della connessione SQL

È possibile controllare il [il timeout della connessione SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) per le istanze di origine e di destinazione durante l'esecuzione di una valutazione o la migrazione, impostando il valore di timeout di connessione a un numero specificato di secondi. Il valore predefinito è 15 secondi.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>Vedere anche

[Download di Assistente per la migrazione dei dati](https://www.microsoft.com/download/details.aspx?id=53595)

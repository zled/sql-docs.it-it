---
title: Librerie di Python | Documenti Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ec0e006a71bb8634b77b83551c9ad82bdb41b246
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="python-libraries-and-data-types"></a>Tipi di dati e le librerie di Python

Questo argomento descrive le librerie Python incluse con i prodotti seguenti:

+ Sul computer Server SQL Learning Services (In-Database)
+ Microsoft Machine Learning Server (Standalone)

In questo argomento elenca anche i tipi di dati non supportato e tipo di dati di elenchi di conversioni che possono essere eseguite in modo implicito quando i dati vengono passati tra Python e SQL Server.

## <a name="python-version"></a>Versione di Python

SQL Server 2017 CTP 2.0 include una parte della distribuzione Anaconda e Python 3.6.

Un subset delle funzionalità RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, forse alcuni altri) è fornita mediante le API di Python, con un nuovo pacchetto di Python **RevoScalePy**. Per funzionare con dati con Pandas i frame di dati, è possibile utilizzare il pacchetto. File con estensione XDF o query di dati SQL.

Per ulteriori informazioni, vedere [revoscalepy che cos'è?](what-is-revoscalepy.md).

## <a name="python-and-sql-data-types"></a>Python e tipi di dati SQL

Python supporta un numero limitato di tipi di dati rispetto a SQL Server.

Di conseguenza, ogni volta che si utilizzano dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] negli script Python, i dati potrebbero essere convertiti in modo implicito in un tipo di dati compatibile. Tuttavia, spesso non è possibile eseguire automaticamente un tipo specifico di conversione e viene restituito un errore.

Questa tabella elenca le conversioni implicite che vengono fornite. Non sono supportati altri tipi di dati.

|SQLtype|Tipo di Python|
|-|-|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|





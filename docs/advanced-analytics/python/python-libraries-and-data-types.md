---
title: Librerie di Python | Documenti Microsoft
ms.custom: ''
ms.date: 03/30/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 14691885d6dcdb91558ddc9566f4320c8119a9dd
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="python-libraries-and-data-types"></a>Tipi di dati e le librerie di Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive le librerie Python incluse con i prodotti seguenti:

+ SQL Server apprendimento Services (In-Database)
+ Microsoft Virtual Server (Standalone) di apprendimento

Questo articolo vengono elencati anche i tipi di dati non supportato e tipo di dati di elenchi di conversioni che possono essere eseguite in modo implicito quando i dati passati tra Python e SQL Server.

## <a name="python-version"></a>Versione di Python

SQL Server 2017 CTP 2.0 include una parte della distribuzione Anaconda e Python 3.6.

Un subset delle funzionalità RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, forse alcuni altri) è fornita mediante le API di Python, utilizzando un nuovo pacchetto di Python **revoscalepy**. È possibile utilizzare questo pacchetto per operare sui dati utilizzando frame di dati Pandas, i file con estensione XDF o le query di dati SQL.

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
|**ntext**|`str`|




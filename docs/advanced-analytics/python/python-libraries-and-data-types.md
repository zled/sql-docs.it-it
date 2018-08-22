---
title: Tipi di dati e le librerie di Python in SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7b977d079589dbb4c54d5c31fec644d9f984dd61
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434851"
---
# <a name="python-libraries-and-data-types"></a>Librerie e tipi di dati Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive le librerie di Python inclusi in SQL Server Machine Learning Services (In-Database) e le installazioni (autonomo).

Questo articolo elenca anche i tipi di dati non supportati e tipo di dati di elenchi di conversioni che possono essere eseguite in modo implicito quando i dati vengono passati tra codice Python e SQL Server.

## <a name="python-version"></a>Versione di Python

Distribuzione di SQL Server 2017 Anaconda 4.2 e in Python 3.6.

Un sottoinsieme delle funzionalità RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, forse alcuni altri) viene fornito tramite le API Python, usando un nuovo pacchetto di Python **revoscalepy**. È possibile usare questo pacchetto per lavorare con i dati usando query di dati SQL, file XDF o frame di dati Pandas.

Per altre informazioni, vedere [What ' s revoscalepy?](what-is-revoscalepy.md).

## <a name="python-and-sql-data-types"></a>Tipi di dati SQL e Python

Python supporta un numero limitato di tipi di dati rispetto a SQL Server.

Di conseguenza, ogni volta che si utilizzano i dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] negli script di Python, i dati potrebbero essere convertiti in modo implicito in un tipo di dati compatibile. Tuttavia, spesso una conversione esatta non può essere eseguita automaticamente e viene restituito un errore.

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




---
title: Tipi di dati di Java supportati in SQL Server 2019 | Microsoft Docs
description: Eseguire il mapping di tipi di dati da Java a SQL Server per le strutture di dati di input e output e per i parametri di input nella finestra di sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3510b53510514daa125382fc10ea33285fe44a80
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715264"
---
# <a name="java-and-sql-server-supported-data-types"></a>Tipi di dati supportati di SQL Server e Java

Questo articolo esegue il mapping di tipi di dati di SQL Server in tipi di dati Java per le strutture di dati e i parametri nel [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Tipi di dati per i set di dati

I seguenti tipi di dati SQL e Java sono attualmente supportati per i set di dati di Input e Output.

| Tipo SQL        | Tipo di Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Stringa (unicode)      | | |
| nvarchar (n) | Stringa (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |

## <a name="data-types-for-input-parameters"></a>Tipi di dati per i parametri di input

I seguenti tipi di dati SQL e Java sono attualmente supportati per i parametri di input.

| Tipo SQL        | Tipo di Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Stringa (unicode)      | | |
| nvarchar (n) | Stringa (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | Stringa (unicode)      | | |
| varbinary(max) | byte[]      | | |

## <a name="see-also"></a>Vedere anche

+ [Come chiamare Java in SQL Server](howto-call-java-from-sql.md)
+ [Esempio di Java in SQL Server](java-first-sample.md)
+ [Estensione del linguaggio Java in SQL Server](extension-java.md)
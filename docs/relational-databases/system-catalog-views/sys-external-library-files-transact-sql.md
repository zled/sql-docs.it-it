---
title: sys.external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ef3ef80905277660af98597cca77132c39222b1
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085164"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Include una riga per ogni file che costituiscono una libreria esterna.

|Nome colonna |Tipo di dati |Description|
|------|------|-----|
|external_library_id | INT |ID dell'oggetto libreria esterna. |
|content |varbinary(max) |Contenuto dell'elemento file libreria esterna. |
|Piattaforma |TINYINT |ID della piattaforma host in cui è installato SQL Server. |
|platform_desc | nvarchar(60) |Nome della piattaforma dell'host. I valori validi sono 'WINDOWS', 'LINUX'. |

### <a name="see-also"></a>Vedere anche  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestione dei pacchetti per il servizio SQL Server Machine Learning](../../advanced-analytics/r/installing-and-managing-r-packages.md)  

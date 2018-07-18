---
title: sys.external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: febfe235bd7f4711e8192ab7625491b72ac050ec
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001173"
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

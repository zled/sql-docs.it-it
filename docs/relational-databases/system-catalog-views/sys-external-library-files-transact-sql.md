---
title: Sys.external_library_files (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.external_library_files catalog view
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: a03a50bdeda18d027fbad56e2cd4b86a261052b7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sysexternallibraryfiles-transact-sql"></a>Sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Elenca una riga per ogni file che costituiscono una libreria esterna.

|Nome colonna |Tipo di dati |Description|
|------|------|-----|
|external_library_id | INT |ID dell'oggetto libreria esterna. |
|content |varbinary(max) |Contenuto dell'elemento file libreria esterna. |
|Piattaforma |TINYINT |ID della piattaforma host in cui è installato SQL Server. |
|platform_desc | nvarchar(60) |Nome della piattaforma host. I valori validi sono 'WINDOWS', 'LINUX'. |

### <a name="see-also"></a>Vedere anche  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREARE UNA LIBRERIA ESTERNA](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestione dei pacchetti per il servizio SQL Server Machine Learning](../../advanced-analytics/r/installing-and-managing-r-packages.md)  

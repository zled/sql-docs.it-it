---
title: Sys.external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1373849201dccbb36f7096549d63864a23330f14
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43075874"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Supporta la gestione delle librerie di pacchetti correlati al runtime esterni, ad esempio R o Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Sys.external_libraries la vista del catalogo include una riga per ogni libreria esterna a cui è stato caricato nel database.

|Nome colonna |Tipo di dati | Description|
|------|------|------|
|external_library_id |INT | ID dell'oggetto libreria esterna. |
|NAME |sysname |Nome della libreria esterna. È univoco all'interno del database per proprietario.|
|principal_id |INT |ID dell'entità che possiede questa libreria esterna. |
|language | sysname | Nome del linguaggio o runtime che supporta la libreria esterna. I valori validi sono 'R'. I runtime aggiuntivi possono essere aggiunti in futuro.|
|ambito |INT |0 per ambito pubblico. 1 per l'ambito privato |  
|scope_desc |varchar(7) |Indica se il pacchetto è pubblica o privata|


## <a name="see-also"></a>Vedere anche  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestione dei pacchetti per SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  

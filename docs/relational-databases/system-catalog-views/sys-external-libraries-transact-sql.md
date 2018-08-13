---
title: Sys.external_libraries (Transact-SQL) | Microsoft Docs
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
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3f6d833488982da777d0f146d55f0a67fa945de5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553261"
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

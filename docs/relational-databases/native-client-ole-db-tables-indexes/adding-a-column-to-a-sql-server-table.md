---
title: Aggiunta di una colonna in una tabella SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0305b23280170613daa17d0f04c3b585edbe6618
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Aggiunta di una colonna a una tabella di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone la **itabledefinition:: AddColumn** (funzione). Ciò consente agli utenti di aggiungere una colonna a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Quando si aggiunge una colonna per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client è vincolato come indicato di seguito:  
  
-   Se DBPROP_COL_AUTOINCREMENT è VARIANT_TRUE, DBPROP_COL_NULLABLE deve essere VARIANT_FALSE.  
  
-   Se la colonna viene definita tramite la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** del tipo di dati, DBPROP_COL_NULLABLE deve essere VARIANT_FALSE.  
  
-   Per qualsiasi altra definizione di colonna, DBPROP_COL_NULLABLE deve essere VARIANT_TRUE.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pTableID* parametro. Il *eKind* membro di *pTableID* deve essere DBKIND_NAME.  
  
 Il nuovo nome di colonna viene specificato come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *dbcid* membro del parametro DBCOLUMNDESC *pColumnDesc*. Il *eKind* membro deve essere DBKIND_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  

---
title: Risultati di SQL Server messaggi | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 371183fab5ba9781a425cc757df895fa7311c6d0
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542232"
---
# <a name="sql-server-message-results"></a>Risultati dei messaggi di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Nell'esempio [!INCLUDE[tsql](../../includes/tsql-md.md)] non generano istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rowset OLE DB provider o un conteggio di righe quando viene eseguito è influenzato:  
  
-   PRINT  
  
-   RAISERROR con gravità minore o uguale a 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Queste istruzioni restituiscono uno o più messaggi informativi o determinano la restituzione da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di messaggi informativi in sostituzione dei risultati del conteggio o del set di righe. Sulla corretta esecuzione, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider restituisce S_OK, e i messaggi sono disponibili per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nativo Client consumer OLE DB provider.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider restituisce S_OK e dispone di uno o più messaggi informativi disponibili dopo l'esecuzione di molti [!INCLUDE[tsql](../../includes/tsql-md.md)] le istruzioni o l'esecuzione del consumer di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] membro provider Client OLE DB nativo funzione.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consumer OLE DB provider consentendo dinamico specifica del testo della query è necessario controllare interfacce degli errori dopo ogni esecuzione della funzione membro indipendentemente dal valore del codice restituito, la presenza o assenza di un restituito**IRowset** o **IMultipleResults** riferimenti all'interfaccia o un numero di righe modificate.  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  

---
title: bcp_batch | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d33b13c8aabeff7c8e8050212a6907bfab4e6cbd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bcpbatch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Esegue il commit di tutte le righe precedentemente bulk copiati dalle variabili di programma e inviate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Il numero di righe salvato dopo l'ultima chiamata a **bcp_batch**, oppure -1 in caso di errore.  
  
## <a name="remarks"></a>Osservazioni  
 I batch della copia bulk definiscono le transazioni. Quando un'applicazione usa [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) e **bcp_sendrow** per copia bulk di righe dalle variabili di programma alle tabelle di SQL Server, vengono eseguito il commit delle righe solo quando il programma chiama **bcp_batch** o [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md).  
  
 È possibile chiamare **bcp_batch** una volta ogni *n* righe o quando c'è una pausa nei dati in entrata (come in un'applicazione telemetrica). Se un'applicazione non chiama **bcp_batch** la copia di massa di righe viene eseguito solo quando **bcp_done** viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

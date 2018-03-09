---
title: bcp_collen | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- bcp_collen
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1528b71e05a77034235606f43c9dc455521d79b1
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="bcpcollen"></a>bcp_collen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Imposta la lunghezza dei dati nella variabile di programma per la copia bulk corrente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_collen (  
        HDBC hdbc,  
        DBINT cbData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *cbData*  
 Lunghezza dei dati nella variabile di programma esclusa la lunghezza dei caratteri di terminazione o degli indicatori di lunghezza. Impostazione *cbData* su SQL_NULL_DATA indica tutte le righe copiate nel server contengono un valore NULL per la colonna. L'impostazione di cbData su SQL_VARLEN_DATA indica che verrà utilizzato un carattere di terminazione della stringa o un altro metodo per determinare la lunghezza dei dati copiati. Se sono presenti sia un indicatore di lunghezza che un carattere di terminazione, il sistema utilizzerà il metodo che comporta la copia del minor numero di dati.  
  
 *idxServerCol*  
 Posizione ordinale della colonna nella tabella in cui vengono copiati i dati. La prima colonna è 1. La posizione ordinale di una colonna è indicata da [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Il **bcp_collen** funzione consente di modificare la lunghezza dei dati nella variabile di programma per una determinata colonna quando si copiano dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Inizialmente, la lunghezza dei dati viene determinata quando [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) viene chiamato. Se viene modificata la lunghezza dei dati tra le chiamate a **bcp_sendrow** e non viene utilizzato alcun prefisso di lunghezza o carattere di terminazione, è possibile chiamare **bcp_collen** per reimpostare la lunghezza. La chiamata successiva a **bcp_sendrow** utilizza la lunghezza impostata dalla chiamata a **bcp_collen**.  
  
 È necessario chiamare **bcp_collen** una volta per ogni colonna della tabella la cui lunghezza dei dati che si desidera modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

---
title: bcp_collen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a66a88a61a581dff262fb8585b5cf32830f8eeed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137971"
---
# <a name="bcpcollen"></a>bcp_collen
  Imposta la lunghezza dei dati nella variabile di programma per la copia bulk corrente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *cbData*  
 Lunghezza dei dati nella variabile di programma esclusa la lunghezza dei caratteri di terminazione o degli indicatori di lunghezza. L'impostazione *cbData* su SQL_NULL_DATA indica tutte le righe copiate nel server contengono un valore NULL per la colonna. L'impostazione di cbData su SQL_VARLEN_DATA indica che verrà utilizzato un carattere di terminazione della stringa o un altro metodo per determinare la lunghezza dei dati copiati. Se sono presenti sia un indicatore di lunghezza che un carattere di terminazione, il sistema utilizzerà il metodo che comporta la copia del minor numero di dati.  
  
 *idxServerCol*  
 Posizione ordinale della colonna nella tabella in cui vengono copiati i dati. La prima colonna è 1. La posizione ordinale di una colonna viene indicata da [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Note  
 Il **bcp_collen** funzione consente di modificare la lunghezza dei dati nella variabile di programma per una determinata colonna quando si copiano dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con [bcp_sendrow](bcp-sendrow.md).  
  
 Inizialmente, la lunghezza dei dati viene determinata quando [bcp_bind](bcp-bind.md) viene chiamato. Se la lunghezza dei dati viene modificata tra le chiamate a **bcp_sendrow** e non viene utilizzato alcun prefisso di lunghezza o carattere di terminazione, è possibile chiamare **bcp_collen** per reimpostare la lunghezza. La chiamata successiva a **bcp_sendrow** utilizza la lunghezza impostata dalla chiamata al metodo **bcp_collen**.  
  
 È necessario chiamare **bcp_collen** una volta per ogni colonna della tabella la cui lunghezza dei dati che si desidera modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

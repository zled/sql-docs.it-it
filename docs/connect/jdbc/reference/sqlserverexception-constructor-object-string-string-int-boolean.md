---
title: Costruttore SQLServerException (lang, lang, lang, int, boolean) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e6e0ef2f83c8dc0641cbaed60e6333590fc9ca1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>Costruttore SQLServerException (lang, lang, lang, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inizializza una nuova istanza del [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe quando viene specificato un **oggetto**, **stringa** oggetto, un **stringa** oggetto, un **int**e un **booleano**.

## <a name="syntax"></a>Sintassi  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            int errNum,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Parametri  
 *obj*  
  
 Il buffer dei / o che ha generato l'eccezione.

 *errText*  
  
 Stringa contenente il testo dell'errore.
  
 *sqlState*  
  
 Un oggetto di enumerazione che contiene lo stato SQL.
 
 *errNum*  
  
 Un valore int che contiene il codice di errore per l'eccezione.
 
 *bStack*  
  
 Valore booleano che indica se la traccia dello stack deve essere generata.
  
## <a name="see-also"></a>Vedere anche  
 [Costruttori di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Membri di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Classe SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  

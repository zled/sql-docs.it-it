---
title: Metodo Cancel (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bd0845e6bebf1365ab8c26cb48bda2a92a6b4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840169"
---
# <a name="cancel-method-sqlserverstatement"></a>Metodo cancel (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annulla l'istruzione SQL attualmente in esecuzione tramite questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo di annullamento viene specificato dal metodo di annullamento nell'interfaccia Statement.  
  
 Quando si esegue un'istruzione che genera un solo set di risultati forward-only di sola lettura di grandi dimensioni, si potrebbe essere interessati solo a qualche set di righe iniziale nel set di risultati restituito. In questo caso, l'applicazione potrebbe chiamare il metodo [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) dell'oggetto istruzione associato prima di chiudere il set di risultati in modo da ridurre al minimo il tempo di elaborazione necessario per rimuovere le righe rimanenti non necessarie. Al momento di decidere se utilizzare o meno questa tecnica, si consiglia di tenere conto della necessità di mantenere un equilibrio tra il tempo di elaborazione salvato e il tempo e il round trip al server aggiuntivo necessari per annullare l'esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

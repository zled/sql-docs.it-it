---
title: Metodo Recover (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ec96cd3f56b1710268ae951e39e98866fe1bd54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826819"
---
# <a name="recover-method-sqlserverxaresource"></a>Metodo recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene un elenco di rami di transazioni preparati da uno strumento di gestione delle risorse.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Parametri  
 *flags*  
  
 Un' **int** valore che può assumere uno dei seguenti valori: XAResource.TMSTARTRSCAN o XAResource.TMENDRSCAN o XAResource.TMNOFLAGS o XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Xid.  
  
## <a name="exceptions"></a>Eccezioni  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Questo metodo recover viene specificato dal metodo recover nell'interfaccia javax.transaction.xa.XAResource.  
  
 Se il parametro **flag** non XAResource.TMSTARTRSCAN o XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, un'analisi di ripristino deve essere in corso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

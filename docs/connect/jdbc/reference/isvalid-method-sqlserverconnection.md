---
title: Metodo isValid (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 855a2fc8c6ff5a1cb9cee1db7504e0dd309113b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727449"
---
# <a name="isvalid-method-sqlserverconnection"></a>Metodo isValid (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) non è stato chiuso ed è ancora valido.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Parametri  
 *timeout*  
  
 Valore **int** che specifica il numero di secondi di attesa per la convalida della connessione.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la connessione è valida; **false** se la connessione non è valida o la validità della connessione non può essere determinata prima che il timeout scada.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo isValid viene specificato dal metodo isValid nell'interfaccia Java.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

---
title: Metodo setLockTimeout (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4d3801e4494ae42cabc1d3ca149669a66273574
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>Metodo setLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un **int** valore che indica il numero di millisecondi di attesa prima che il database segnali un timeout di blocco.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Parametri  
 *lockTimeout*  
  
 Un **int** valore che contiene il numero di millisecondi di attesa.  
  
## <a name="remarks"></a>Osservazioni  
 Il timeout di blocco è il numero di millisecondi di attesa prima che venga segnalato un timeout di blocco per il database. Il valore predefinito -1 indica un'attesa illimitata. Se specificato, questo valore diventerà l'impostazione predefinita per tutte le istruzioni sulla connessione.  
  
> [!NOTE]  
>  Un valore pari a 0 indica che non vi sarà attesa. Se la proprietà lockTimeout non è impostata, il [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) il metodo restituisce il valore predefinito-1.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  


---
title: Metodo setPortNumber (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26f5f9e97d086e64f008c7f4af2913a5305585a1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setportnumber-method-sqlserverdatasource"></a>Metodo setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di porta da utilizzare per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parametri  
 *numero di porta*  
  
 Un **int** valore che contiene il numero di porta.  
  
## <a name="remarks"></a>Osservazioni  
 Il numero di porta è il numero di porta TCP/IP viene utilizzato quando si apre una connessione socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Se la proprietà portNumber non è impostata, il [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) il metodo restituisce il valore predefinito 1433.  
  
> [!NOTE]  
>  Il metodo setPortNumber non esegue alcun controllo sul valore di porta passato di intervallo. È possibile passare un numero di porta che non è valido, come 99999, senza generare un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

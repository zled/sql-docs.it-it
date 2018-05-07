---
title: Metodo setPortNumber (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5665bd5ed6f10a755f3980607995b19887908379
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Metodo setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di porta da utilizzare per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Numero di porta*  
  
 Un **int** valore che contiene il numero di porta.  
  
## <a name="remarks"></a>Osservazioni  
 Il numero di porta è il numero di porta TCP/IP viene utilizzato quando si apre una connessione socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Se la proprietà portNumber non è impostata, il [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) il metodo restituisce il valore predefinito 1433.  
  
> [!NOTE]  
>  Il metodo setPortNumber non esegue alcun controllo sul valore di porta passato di intervallo. È possibile passare un numero di porta che non è valido, come 99999, senza generare un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

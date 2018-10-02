---
title: Metodo getPortNumber (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30b2387b4685440de737ad9e6be7d351ded86506
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736635"
---
# <a name="getportnumber-method-sqlserverdatasource"></a>Metodo getPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il numero della porta corrente usata per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** contenente il numero di porta corrente.  
  
## <a name="remarks"></a>Remarks  
 Il numero di porta è il numero di porta TCP/IP usato quando si apre una connessione socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se la proprietà portNumber non è impostata, il metodo getPortNumber restituisce il valore predefinito 1433.  
  
> [!NOTE]  
>  Il [setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) metodo non esegue alcun controllo sul valore di porta passato di intervallo. È possibile passare numeri che non sono validi, come 99999, senza generare un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

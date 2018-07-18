---
title: Metodo setSelectMethod (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a4de6cbf75816c584add43b3bfc1d9415f79f94
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843996"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Metodo setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Parametri  
 *selectMethod*  
  
 Oggetto **stringa** valore contenente il tipo di cursore predefinito.  
  
## <a name="remarks"></a>Osservazioni  
 selectMethod è il tipo di cursore predefinito utilizzato per un set di risultati. Questa proprietà è utile in caso di set di risultati di grandi dimensioni e se non desidera archiviare tutto il set di risultati in memoria nel lato client. Impostando la proprietà su "cursor", è possibile creare un cursore sul lato server che può recuperare i blocchi di dati più piccoli in una sola volta. Se la proprietà selectMethod non è impostata, [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) restituisce il valore predefinito "Direct".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

---
title: Metodo (SQLServerDataSource) setTrustManagerConstructorArg | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setTrustManagerConstructorArg
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77d950490d5792a39a454c30fda2a03cdbb8ba22
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845556"
---
# <a name="settrustmanagerconstructorarg-method-sqlserverdatasource"></a>setTrustManagerConstructorArg metodo (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore di stringa della proprietà di connessione TrustManagerConstructorArg.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustManagerConstructorArg(java.lang.String trustManagerClass)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustManagerClass*  
  
 Oggetto **stringa** che contiene il nome classe completo di un javax.net.ssl.TrustManager personalizzato.
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

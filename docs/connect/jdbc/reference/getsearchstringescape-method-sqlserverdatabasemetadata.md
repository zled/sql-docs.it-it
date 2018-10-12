---
title: Metodo getSearchStringEscape (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a12b9ca70dd8e48fa92df9b1b2be55b22ee6994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721359"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Metodo getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore **String** che può essere usato come escape per i caratteri jolly.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String** contenente la stringa di carattere jolly di escape.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getSearchStringEscape viene specificato dal metodo getSearchStringEscape nell'interfaccia DatabaseMetaData.  
  
 Questo metodo viene utilizzato solo per le ricerche con criteri di metadati. Restituisce "\\". Un criterio di ricerca **String** può usare la sequenza di escape per i caratteri jolly ("%" e "_") e fornirli come valori letterali anteponendo una barra rovesciata. In questo modo, "\\%" viene convertito in "[%]" e "\\\_" viene convertito in "[\_]".  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

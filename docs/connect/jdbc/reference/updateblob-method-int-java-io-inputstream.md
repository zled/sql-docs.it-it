---
title: Metodo updateBlob (int, Java.IO. InputStream) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0263018-d326-4a7b-bf6f-5f508db899d4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 190269911011e132450dc44abc4148c0620db340
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850206"
---
# <a name="updateblob-method-int-javaioinputstream"></a>Metodo updateBlob (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata tramite il flusso di input specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *inputStream*  
  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateBlob viene specificato dal metodo updateBlob nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBlob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

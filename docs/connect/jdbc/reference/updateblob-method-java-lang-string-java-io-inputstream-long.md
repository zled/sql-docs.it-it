---
title: Metodo updateBlob (lang, Java.IO. InputStream, long) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f75549-5d5a-4de3-a271-4b8f0dd7b124
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74cbd78a019980e8348016c9880d3bef9b754a5a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updateblob-method-javalangstring-javaioinputstream-long"></a>Metodo updateBlob (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata tramite il flusso di input specificato, che conterrà il numero specificato di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
                                              long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che contiene l'etichetta di colonna.  
  
 *inputStream*  
  
 Un oggetto InputStream.  
  
 *length*  
  
 Oggetto **lungo** che indica la lunghezza del flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateBlob viene specificato dal metodo updateBlob nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBlob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

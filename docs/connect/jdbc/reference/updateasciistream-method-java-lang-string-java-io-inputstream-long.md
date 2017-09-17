---
title: Metodo (Java.IO. InputStream, long) updateAsciiStream | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d426e8b9-62b7-49f8-9863-8697fd3a7085
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d8f10f0f2cda308348db6c654bb35a62c1db333
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updateasciistream-method-javalangstring-javaioinputstream-long"></a>Metodo updateAsciiStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso ASCII, che conterrà il numero specificato di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateAsciiStream(java.lang.String columnName,  
                              java.io.InputStream streamValue,  
                              long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *streamValue*  
  
 Un oggetto InputStream.  
  
 *length*  
  
 Lunghezza del flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateAsciiStream viene specificato dal metodo updateAsciiStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri ASCII (byte) da un oggetto InputStream alle colonne di tipo carattere convertibili, l'intervallo ASCII [0x00 – 0x7F] di Unicode e 874, 932, 936, 949, 950 e 1250 a 1258 tabelle codici. Esegue una conversione nella pagina delle regole di confronto di destinazione. Se si tenta di aggiornare una colonna di destinazione non convertibile, verrà generata un'eccezione. Per le colonne binarie, vengono passati byte non elaborati.  
  
 Se la lunghezza del flusso è diversa rispetto a quello specificato nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [updateAsciiStream metodo &#40;java.lang.String, Java.IO. InputStream &#41;](../../../connect/jdbc/reference/updateasciistream-method-java-lang-string-java-io-inputstream.md) quando l'applicazione deve aggiornare la colonna da un flusso la cui lunghezza è sconosciuto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateAsciiStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

---
title: Metodo (Java.IO. InputStream) updateAsciiStream | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dcc3d4f-ae30-45c0-afad-a531358807af
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75801b90ff309c4721c382d7ad355d23f2b78f6d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updateasciistream-method-int-javaioinputstream"></a>Metodo updateAsciiStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso ASCII.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateAsciiStream viene specificato dal metodo updateAsciiStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri ASCII (byte) da un oggetto InputStream alle colonne di tipo carattere convertibili, l'intervallo ASCII [0x00 – 0x7F] di Unicode e 874, 932, 936, 949, 950 e 1250 a 1258 tabelle codici. Esegue una conversione nella pagina delle regole di confronto di destinazione. Se si tenta di aggiornare una colonna di destinazione non convertibile, verrà generata un'eccezione. Per le colonne binarie, vengono passati byte non elaborati.  
  
 Questo metodo per il **immagine**, **testo**, e **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati potrebbero influire sulle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateAsciiStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

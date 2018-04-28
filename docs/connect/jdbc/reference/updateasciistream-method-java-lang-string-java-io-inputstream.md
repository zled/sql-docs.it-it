---
title: Metodo (Java.IO. InputStream) updateAsciiStream | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 747b0308-1ce6-4eba-bdfc-af29c21c18cf
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a78cb79bea80c5c4934de21fedfdeeb6092c6945
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="updateasciistream-method-javalangstring-javaioinputstream"></a>Metodo updateAsciiStream (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso ASCII.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateAsciiStream(java.lang.String columnLabel,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che contiene l'etichetta di colonna.  
  
 *x*  
  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateAsciiStream viene specificato dal metodo updateAsciiStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri ASCII (byte) da un oggetto InputStream alle colonne di tipo carattere convertibili, l'intervallo ASCII [0x00 – 0x7F] di Unicode e 874, 932, 936, 949, 950 e 1250 a 1258 tabelle codici. Esegue una conversione nella pagina delle regole di confronto di destinazione. Se si tenta di aggiornare una colonna di destinazione non convertibile, verrà generata un'eccezione. Per le colonne binarie, vengono passati byte non elaborati.  
  
 Questo metodo per il **immagine**, **testo**, e **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati potrebbero influire sulle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

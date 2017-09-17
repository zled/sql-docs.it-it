---
title: Metodo (Java.IO. InputStream) updateBinaryStream | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56883144-26a0-4f45-ad36-4f616369af3e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1fa688afc52a05664525a165930dca7ed7ac4b49
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream"></a>Metodo updateBinaryStream (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso binario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
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
 Questo metodo updateBinaryStream viene specificato dal metodo updateBinaryStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo per il **immagine**, **testo**, e **ntext** tipi di dati di SQL Server potrebbero compromettere le prestazioni.  
  
 Questo metodo passa byte da un oggetto InputStream selezionare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] colonne binarie quali binary, varbinary, varbinary (max), image, xml e udt. L'aggiornamento delle colonne di tipo carattere non è supportato con questo metodo. Per aggiornare colonne di tipo carattere con un InputStream, utilizzare il [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBinaryStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

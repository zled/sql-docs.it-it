---
title: Metodo updateCharacterStream (lang, Java.IO. Reader) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4738e48f37f05d60f7568b3706f74396982f2c69
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updatecharacterstream-method-javalangstring-javaioreader"></a>Metodo updateCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che contiene l'etichetta di colonna.  
  
 *lettore*  
  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateCharacterStream viene specificato dal metodo updateCharacterStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri Unicode da un oggetto lettore a colonne binarie o di testo selezionata. Questo include tutte le colonne di testo e **binario**, **varbinary**, **varbinary (max)**, **immagine**, e **xml**colonne, ma non **udt** colonne.  
  
 Questo metodo per il **immagine**, **testo**, e **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati potrebbero influire sulle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  


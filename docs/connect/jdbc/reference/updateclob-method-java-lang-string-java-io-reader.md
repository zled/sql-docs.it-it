---
title: Metodo updateClob (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 338a2bf2-b110-469d-ad08-a0f2bbefcb88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f58bee8fa6bc36ea7bae17ee6f432a26b7c288ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799079"
---
# <a name="updateclob-method-javalangstring-javaioreader"></a>Metodo updateClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata mediante l'oggetto Reader specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateClob(java.lang.String columnLabel,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Valore **String** contenente l'etichetta della colonna.  
  
 *reader*  
  
 Oggetto lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateClob viene specificato dal metodo nell'interfaccia ResultSet updateClob.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

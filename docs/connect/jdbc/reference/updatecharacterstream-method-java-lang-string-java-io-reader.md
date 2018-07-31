---
title: Metodo updateCharacterStream (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9c755a658b0a63966a2db4be4e55b09b1004a0a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982513"
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
  
 Valore **String** contenente l'etichetta della colonna.  
  
 *reader*  
  
 Oggetto lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateCharacterStream viene specificato dal metodo updateCharacterStream nell'interfaccia ResultSet.  
  
 Questo metodo passa caratteri Unicode da un oggetto Reader alle colonne di testo e binarie selezionate. Include tutte le colonne di testo e le colonne **binary**, **varbinary**, **varbinary(max)**, **image** e **xml**, ma non le colonne **udt**.  
  
 Utilizzo di questo metodo per la **immagine**, **testo**, e **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] i tipi di dati potrebbero influire sulle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

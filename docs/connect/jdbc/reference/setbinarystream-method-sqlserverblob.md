---
title: Metodo setBinaryStream (SQLServerBlob) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: abcec31f-1a60-4765-9725-8cf7e9f1f8ab
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0c32868257eeebc4cfc24945d853e1440e34ee78
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841206"
---
# <a name="setbinarystream-method-sqlserverblob"></a>Metodo setBinaryStream (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un flusso che può essere utilizzato per scrivere nel valore BLOB.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.OutputStream setBinaryStream(long pos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione nel valore BLOB in corrispondenza della quale iniziare la scrittura.  
  
## <a name="return-value"></a>Valore restituito  
 Flusso di output.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setBinaryStream viene specificato dal metodo setBinaryStream nell'interfaccia Java.SQL. BLOB.  
  
 I dati nel valore BLOB vengono sovrascritti dal flusso di output a partire dalla posizione specificata e possono superare la lunghezza iniziale di tale valore. Se si specifica un valore posizione+1, verranno aggiunti byte. Se si passa un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

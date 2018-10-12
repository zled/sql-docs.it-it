---
title: Metodo setCharacterStream (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 081da23826951c5c8c4d4872de1c28a771a2958b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720919"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>Metodo setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un flusso da usare per scrivere un flusso di caratteri Unicode nel valore **NCLOB** rappresentato da questo oggetto **java.sql.NClob**, a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione di inizio della scrittura nel valore **NCLOB**. La prima posizione è 1.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Writer che rappresenta il flusso in cui possono essere scritti i caratteri Unicode.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setCharacterStream viene specificato dal metodo nell'interfaccia java.sql.NClob setCharacterStream.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

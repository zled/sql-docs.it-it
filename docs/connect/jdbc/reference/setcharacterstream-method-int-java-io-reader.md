---
title: Metodo setCharacterStream (int, Java.IO. Reader) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fa0e3edcc88e105f631105fb6d3735c6baa6348
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843456"
---
# <a name="setcharacterstream-method-int-javaioreader"></a>Metodo setCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto specificato Java.IO. Reader.  
  
> [!NOTE]  
>  Questa funzionalità è stata introdotta con la [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC versione 2.0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Un **int** che indica il numero di parametro.  
  
 *Lettore*  
  
 Oggetto che contiene i dati Unicode Java.IO. Reader.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCharacterStream viene specificato dal metodo setCharacterStream nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setCharacterStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  

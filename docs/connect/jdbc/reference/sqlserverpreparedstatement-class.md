---
title: Classe SQLServerPreparedStatement | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c7b37e26faedf7cb064880d68e17f4688bfbe73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32847026"
---
# <a name="sqlserverpreparedstatement-class"></a>Classe SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta l'implementazione di base della funzionalità dell'istruzione preparata di JDBC.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** SQLServerStatement  
  
 **Implementa:** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Osservazioni  
 SQLServerPreparedStatement fornisce metodi che consentono di fornire i parametri come qualsiasi tipo nativo di Java e molti tipi di oggetto Java. SQLServerPreparedStatement prepara un'istruzione tramite il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **sp_prepare** stored procedure, quindi riutilizza handle di istruzione restituito per ogni successiva in esecuzione dell'istruzione, in genere utilizzando i diversi parametri forniti dall'utente.  
  
 SQLServerPreparedStatement supporta l'invio in batch, in cui un set di istruzioni preparate viene eseguito in un singolo database round trip per migliorare le prestazioni di runtime.  
  
 Questa classe supporta l'annullamento del wrapping nella classe SQLServerPreparedStatement, ISQLServerPreparedStatement, interfaccia, l'interfaccia Java.SQL. PreparedStatement e le classi e le interfacce supportate da SQLServerStatement per l'annullamento del wrapping. Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

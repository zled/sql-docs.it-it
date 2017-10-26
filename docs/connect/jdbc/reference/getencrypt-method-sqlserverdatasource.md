---
title: Metodo getEncrypt (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8edaf27e2c08b1738d8dedc3e059c0fecb5043b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getencrypt-method-sqlserverdatasource"></a>Metodo getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **booleano** valore che indica se la proprietà di crittografia è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la crittografia è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] assicura che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizza la crittografia SSL per tutti i dati inviati tra il client e il server se il server è installato un certificato.  
  
 Se la proprietà di crittografia non viene specificata o impostata su **false**, il driver non imporrà la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] per supportare la crittografia SSL. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza non è configurata per forzare la crittografia SSL, viene stabilita una connessione senza crittografia. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza è configurata per forzare la crittografia SSL, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] verrà automaticamente abilita la crittografia SSL quando eseguono correttamente configurato Java Virtual Machine (JVM), altrimenti la connessione viene terminata e il driver genera un errore. Se la proprietà di crittografia non è impostata, il [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) il metodo restituisce il valore predefinito di **false**.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  


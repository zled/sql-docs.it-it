---
title: Metodo setEncrypt (SQLServerDataSource) | Documenti Microsoft
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
apiname:
- setEncrypt Method (SQLServerDataSource)
apilocation:
- setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2277daf4b578c4650c75e55b2a6c63ee3e5d938a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setencrypt-method-sqlserverdatasource"></a>Metodo setEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un **booleano** valore che indica se la proprietà di crittografia è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Crittografare*  
  
 **true** se la crittografia Secure Sockets Layer (SSL) è abilitata tra il client e il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] assicura che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utilizza la crittografia SSL per tutti i dati inviati tra client e server, se il server è installato un certificato. Il valore predefinito è **false**.  
  
 Il driver JDBC rileva l'ambiente Java Virtual Machine (JVM) in cui viene eseguito durante il tentativo di stabilire un handshake SSL.  
  
 Se la proprietà encrypt è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Usa provider di sicurezza JSSE predefinito di JVM per negoziare la crittografia SSL con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. È possibile che il provider di sicurezza predefinito non supporti tutte le funzionalità necessarie per negoziare la crittografia SSL. Ad esempio, il provider di sicurezza predefinito non può supportare la dimensione della chiave pubblica RSA utilizzata nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL. In questo caso, è possibile che venga generato un errore dal provider di sicurezza predefinito, a causa del quale la connessione viene terminata dal driver JDBC. Per risolvere il problema, eseguire una delle operazioni seguenti:  
  
-   Configurare il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] con un certificato server con una chiave pubblica RSA più piccola  
  
-   Configurare JVM per l'utilizzo di un provider di sicurezza JSSE diverso nel "\<java-home > / lib/security/java.security" file delle proprietà di sicurezza  
  
-   Utilizzare una versione di JVM diversa.  
  
 Se la proprietà di crittografia non viene specificata o impostata su **false**, il driver non imporrà la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] per supportare la crittografia SSL. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza non è configurata per forzare la crittografia SSL, viene stabilita una connessione senza crittografia. Se il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza è configurata per forzare la crittografia SSL, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] verrà automaticamente abilita la crittografia SSL quando eseguono correttamente configurato JVM, altrimenti la connessione viene terminata e il driver genererà un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

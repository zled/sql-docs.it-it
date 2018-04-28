---
title: Metodo setIntegratedSecurity (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 320db4baa925a55039623180d092dd3845e0d691
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>Metodo setIntegratedSecurity (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un **booleano** valore che indica se la proprietà integratedSecurity è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Abilitare*  
  
 **true** se integratedSecurity è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Impostare su "**true**" per indicare che le credenziali di Windows da utilizzare per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] per autenticare l'utente dell'applicazione. Se "**true**", il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] cercherà cache delle credenziali le credenziali che sono già state fornite per l'accesso a computer o in rete al computer locale. Se "**false**", è necessario specificare il nome utente e password.  
  
> [!NOTE]  
>  Questa proprietà è supportata solo su [!INCLUDE[msCoName](../../../includes/msconame_md.md)] sistemi operativi Windows.  
  
 Per ulteriori informazioni sull'utilizzo dell'autenticazione integrata, vedere [creazione dell'URL di connessione](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

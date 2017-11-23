---
title: Metodo getReference (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.getReference
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0d24fa8c02c24c8d35a031bf0e7b49c35b12424
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getreference-method-sqlserverdatasource"></a>Metodo getReference (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un riferimento a questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto di riferimento.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getReference viene specificato dal metodo getReference nell'interfaccia javax.  
  
 Prima di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0, se Settruststorepassword veniva chiamato su un oggetto SQLServerDataSource, la password sarebbe stata disponibile nell'oggetto restituito da sqlserverdatasource. GetReference, consentendone l'oggetto da utilizzare per eseguire connessioni aggiuntive. Nel driver JDBC 3.0 sarà necessario impostare la password sull'oggetto restituito da SQLServerDataSource.getReference, prima di eseguire connessioni con l'oggetto.  
  
 Inoltre, se si imposta SQLServerDataSource.setTrustStorePassword prima di associare le proprietà delle origini dati, la chiamata a SQLServerDataSource.setTrustStorePassword deve essere effettuata prima di ottenere la connessione. Ad esempio,  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

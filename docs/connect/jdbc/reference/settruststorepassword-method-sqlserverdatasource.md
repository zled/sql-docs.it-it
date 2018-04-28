---
title: Metodo setTrustStorePassword (SQLServerDataSource) | Documenti Microsoft
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
- setTrustStorePassword Method (SQLServerDataSource)
apilocation:
- setTrustStorePassword Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: fa87cbde-71cc-4f21-bc07-f8ba2b6a0a3f
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ade19dfb72ecdabaa0c20866b3f9d7b36188e372
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="settruststorepassword-method-sqlserverdatasource"></a>Metodo setTrustStorePassword (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la password utilizzata per verificare l'integrità dei dati del file trustStore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustStorePassword(java.lang.String trustStorePassword)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustStorePassword*  
  
 Oggetto **stringa** che contiene la password utilizzata per controllare l'integrità dei dati del file trustStore.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile specificare la proprietà trustStorePassword insieme alla proprietà trustStore in modo da utilizzarne il valore per verificare l'integrità del file trustStore.  
  
 Se è impostata solo la proprietà trustStore e non la proprietà trustStorePassword, l'integrità del file trustStore non viene verificata.  
  
 Quando entrambe le proprietà trustStore e trustStorePassword non sono specificate, il driver utilizza le proprietà di sistema JVM (Java Virtual Machine) "javax.net.ssl.trustStore" e "javax.net.ssl.trustStorePassword". Se la proprietà di sistema "javax.net.ssl.trustStorePassword" non è specificata, l'integrità del file trustStore non viene verificata.  
  
 Se la proprietà trustStore non è impostata ma la proprietà trustStorePassword è impostata, il driver JDBC utilizza il file specificato da "javax.net.ssl.trustStore" come archivio di attendibilità e l'integrità dell'archivio di attendibilità viene verificata utilizzando la proprietà trustStorePassword specificata. Questo può essere necessario quando non si desidera che per l'applicazione client la password venga archiviata nella proprietà di sistema JVM.  
  
 Per ulteriori informazioni, vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 A partire dal driver JDBC 3.0, se si imposta SQLServerDataSource.setTrustStorePassword prima di associare le proprietà delle origini dati, è necessario chiamare SQLServerDataSource.setTrustStorePassword prima di ottenere la connessione. Per ulteriori informazioni, vedere [GetReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

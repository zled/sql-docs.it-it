---
title: "Impostazione dei dati delle proprietà dell'origine | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e49d68f567f26e852dcf8bee3a9827797c9c23f2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-data-source-properties"></a>Impostazione delle proprietà delle origini dei dati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le origini dati sono il meccanismo ideale con cui creare connessioni JDBC in un ambiente Java EE (Java Platform, Enterprise Edition). Le origini dati forniscono connessioni, connessioni in pool e connessioni distribuite senza la necessità di specificare le proprietà di connessione a livello di codice Java. Tutti [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] impostare o ottenere il valore di qualsiasi proprietà utilizzando rispettivamente le impostazione appropriato e i metodi di richiamo, origini dati.  
  
 I prodotti Java EE, quali server applicazioni e motori servlet/JSP, consentono in genere di configurare origini dati per l'accesso ai database. Tutte le proprietà elencate nel [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) argomento può essere specificato ovunque la configurazione consente di immettere una proprietà come proprietà = coppia valore.  
  
 Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] origini dati, vedere il [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe. Per un esempio di come utilizzare la classe SQLServerDataSource per stabilire una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database, vedere [origine dati di esempio](../../connect/jdbc/data-source-sample.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il Driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  


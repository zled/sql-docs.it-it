---
title: Gestione dei metadati con il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63d691c8bef93ad734a7596532ba567708128a2d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Gestione dei metadati con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] può essere utilizzato per operare con i metadati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database in diversi modi. Il driver JDBC può essere utilizzato per estrarre i metadati del database, un set di risultati o parametri.  
  
 Il driver JDBC fornisce tre classi per il recupero dei metadati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), che viene utilizzata per restituire informazioni sul database di cui è attualmente connesso.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), che viene utilizzata per restituire informazioni sul set di risultati.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), che viene utilizzata per restituire informazioni sui parametri di istruzioni preparate e richiamabili.  
  
 Negli argomenti di questa sezione viene descritto come utilizzare ognuna delle tre classi di metadati per gestire metadati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
> [!NOTE]  
>  I metodi per metadati illustrati in questa sezione sono in genere dispendiosi in termini di prestazioni dell'applicazione e si consiglia pertanto di utilizzarli con molta attenzione.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Utilizzo dei metadati del Database](../../connect/jdbc/using-database-metadata.md)|Viene descritto come recuperare i metadati relativi al database con connessione attiva.|  
|[Utilizzo Set di risultati dei metadati](../../connect/jdbc/using-result-set-metadata.md)|Viene descritto come recuperare i metadati relativi al set di risultati corrente.|  
|[Utilizzando i metadati del parametro](../../connect/jdbc/using-parameter-metadata.md)|Viene descritto come recuperare i metadati sui parametri di istruzioni CallableStatement.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  


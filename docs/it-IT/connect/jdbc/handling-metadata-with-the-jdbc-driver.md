---
title: Gestione dei metadati con il Driver JDBC | Documenti Microsoft
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
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f566739dabdda602fcde3bf9726808536a8fb00d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Gestione dei metadati con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] può essere utilizzato per operare con i metadati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database in diversi modi. Il driver JDBC può essere utilizzato per estrarre i metadati del database, un set di risultati o parametri.  
  
 Il driver JDBC fornisce tre classi per il recupero dei metadati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), che consente di restituire informazioni sul database a cui è attualmente connesso.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), che consente di restituire informazioni sui set di risultati.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), che consente di restituire informazioni sui parametri delle istruzioni preparate e richiamabili.  
  
 Negli argomenti di questa sezione viene descritto come utilizzare ognuna delle tre classi di metadati per gestire metadati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
> [!NOTE]  
>  I metodi per metadati illustrati in questa sezione sono in genere dispendiosi in termini di prestazioni dell'applicazione e si consiglia pertanto di utilizzarli con molta attenzione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Uso dei metadati del database](../../connect/jdbc/using-database-metadata.md)|Viene descritto come recuperare i metadati relativi al database con connessione attiva.|  
|[Uso dei metadati del set di risultati](../../connect/jdbc/using-result-set-metadata.md)|Viene descritto come recuperare i metadati relativi al set di risultati corrente.|  
|[Uso dei metadati di parametro](../../connect/jdbc/using-parameter-metadata.md)|Viene descritto come recuperare i metadati sui parametri di istruzioni CallableStatement.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

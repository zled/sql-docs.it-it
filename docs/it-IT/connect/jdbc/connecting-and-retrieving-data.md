---
title: La connessione e il recupero dei dati | Documenti Microsoft
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
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd98a0b7954f5b67bedbaa09833b72d8f5914921
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-and-retrieving-data"></a>Connessione e recupero dei dati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si lavora con la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], sono disponibili due metodi principali per stabilire una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Uno consiste nell'impostare le proprietà di connessione nell'URL della connessione e quindi chiamare il metodo getConnection della classe DriverManager per restituire un [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
> [!NOTE]  
>  Per un elenco delle proprietà di connessione supportate dal driver JDBC, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Il secondo metodo consente di impostare le proprietà di connessione utilizzando i metodi di impostazione del [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe e chiamando quindi il [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) per restituire un SQLServerConnection oggetto.  
  
 Negli argomenti di questa sezione vengono descritti i diversi modi in cui è possibile connettersi a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e vengono inoltre illustrate diverse tecniche per il recupero dei dati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Esempio di URL di connessione](../../connect/jdbc/connection-url-sample.md)|Viene descritto come utilizzare un URL di connessione per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e quindi utilizzare un'istruzione SQL per recuperare i dati.|  
|[Esempio di origine dati](../../connect/jdbc/data-source-sample.md)|Viene descritto come utilizzare un'origine dati per connettersi a SQL Server e quindi utilizzare una stored procedure per il recupero dei dati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni di esempio del driver JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  

---
title: Creazione di applicazioni con SQL Server Native Client | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b0c37dc63016fca1add0a78342eaa3d0f74cd18a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="building-applications-with-sql-server-native-client"></a>Compilazione di applicazioni con SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Lo sviluppo di un'applicazione che utilizza la libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client comporta una serie di problemi di cui tenere conto. Negli argomenti di questa sezione vengono illustrati alcuni dei problemi riscontrati, incluso l'aggiornamento da MDAC a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e l'utilizzo dei file di intestazione e di libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e viene fornita una panoramica delle varie stringhe di connessione che è possibile utilizzare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Installazione di SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 Vengono descritti l'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, i percorsi di installazione dei vari componenti e la disinstallazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Componenti di SQL Server Native Client](../../../relational-databases/native-client/applications/components-of-sql-server-native-client.md)  
 Vengono illustrati i componenti che costituiscono [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, inclusi i file di libreria, di risorse, della Guida e di intestazione.  
  
 [Utilizzo di Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
 Vengono illustrati i vari tipi di stringhe di connessione che è possibile utilizzare durante la connessione a un database tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Utilizzando i file di libreria e l'intestazione SQL Server Native Client](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)  
 Viene illustrato come utilizzare i file di intestazione e di libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client all'interno di un'applicazione.  
  
 [Aggiornamento di un'applicazione a SQL Server Native Client da MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)  
 Vengono illustrate le differenze tra [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e MDAC e vengono descritti i problemi di cui tenere conto durante l'aggiornamento da MDAC a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Aggiornamento di un'applicazione da SQL Server 2005 Native Client](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)  
 Vengono illustrati i problemi di cui tenere conto durante l'aggiornamento da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Utilizzo di ADO con SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md)  
 Viene illustrato l'utilizzo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client da parte di ADO per accedere alla funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e utilizzarla.  
  
 [Criteri di supporto per SQL Server Native Client](../../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md)  
 Viene illustrato in che modo è possibile utilizzare i vari componenti di accesso ai dati con diverse versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Connessione a un database SQL di Microsoft Azure con SQL Server Native Client](../../../relational-databases/native-client/applications/connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 Viene illustrato come connettersi a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] mediante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Procedure ODBC](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Procedure per OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

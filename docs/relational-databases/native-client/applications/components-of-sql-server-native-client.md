---
title: Componenti di SQL Server Native Client | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cb812cc6b820af30439f811d078e955cf56aa1dd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="components-of-sql-server-native-client"></a>Componenti di SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono inclusi i componenti seguenti:  
  
|Componente|Description|  
|---------------|-----------------|  
|sqlncli11.dll|File della libreria di collegamento dinamico (DLL) che contiene tutte le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sono inclusi il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|File di risorse associato per la libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|   
|sqlncli.h|File di intestazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client che contiene tutte le nuove definizioni necessarie per utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Questo file di intestazione sostituisce entrambi i file di intestazione, odbcss.h e sqloledb.h.<br /><br /> Nota: È possibile fare riferimento a SQLNCLI. h e Odbcss. h nello stesso programma, ma è possibile fare riferimento SQLNCLI. h e SQLOLEDB. h nello stesso programma, purché SQLOLEDB viene dapprima definita.|  
|sqlncli11.lib|Il file di libreria necessario per chiamare direttamente il **bcp** funzioni di utilità che fanno parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client.<br /><br /> Nota: Se si fa riferimento al file sqlncli11.lib nel codice di programmazione, è necessario assicurarsi che il file sqlncli11.dll sia nel percorso di sistema e nel percorso di sistema di utenti che utilizzano l'applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  

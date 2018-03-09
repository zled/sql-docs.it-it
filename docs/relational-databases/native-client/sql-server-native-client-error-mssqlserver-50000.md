---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ebd08bda56c89fd219b124244d5ba7a0254142d5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>Errore di SQL Server Native Client MSSQLSERVER_50000
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|Versione prodotto|11.0|  
|ID evento|50000|  
|Origine evento|SETUP|  
|Componente|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Nome simbolico||  
|Testo del messaggio|Errore di rete durante il tentativo di lettura dal file '%. * ls.'|  
  
## <a name="explanation"></a>Spiegazione  
 È stato eseguito il tentativo di installare (o aggiornare) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in un computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è già stato installato da un file MSI che è stato rinominato da sqlncli.msi.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere il problema, disinstallare la versione esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Per prevenire questo errore, non installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client da un file MSI non denominato sqlncli.msi.  
  
## <a name="internal-only"></a>Solo interno  
  

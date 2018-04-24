---
title: Controllare la versione dei driver ODBC di SQL Server (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1012d97082fe975a4e5eea7e0003df703ad32bc0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Verifica della versione dei driver ODBC di SQL Server (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  È possibile che nel computer siano installati numerosi driver ODBC di [!INCLUDE[msCoName](../../includes/msconame-md.md)] e di altre società. Questo argomento descrive come usare **Amministratore origine dati ODBC** di Windows per verificare la versione dei driver ODBC installati.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Per verificare la versione dei driver ODBC di SQL Server (ODBC a 32 bit)  
  
-   In **Amministratore origine dati ODBC**selezionare la scheda **Driver** .  
  
     Le informazioni relative alla voce Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno visualizzate nella colonna **Versione** .  


> [!NOTE]  
>  Per le connessioni all'autenticazione di Azure Active Directory per il database SQL, installare il driver più recente, ad esempio il [driver ODBC 13.1 per SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a>Vedere anche  
 [Apertura di Amministratore origine dati ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  

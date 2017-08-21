---
title: Controllare la versione dei driver ODBC di SQL Server (Windows) | Microsoft Docs
ms.custom: 
ms.date: 11/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fc0d054304aadb3f5c8df795dca4ad327090e5c1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Verifica della versione dei driver ODBC di SQL Server (Windows)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  È possibile che nel computer siano installati numerosi driver ODBC di [!INCLUDE[msCoName](../../includes/msconame-md.md)] e di altre società. Questo argomento descrive come usare **Amministratore origine dati ODBC** di Windows per verificare la versione dei driver ODBC installati.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Per verificare la versione dei driver ODBC di SQL Server (ODBC a 32 bit)  
  
-   In **Amministratore origine dati ODBC**selezionare la scheda **Driver** .  
  
     Le informazioni relative alla voce Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno visualizzate nella colonna **Versione** .  


> [!NOTE]  
>  Per le connessioni all'autenticazione di Azure Active Directory per il database SQL, installare il driver più recente, ad esempio il [driver ODBC 13.1 per SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a>Vedere anche  
 [Apertura di Amministratore origine dati ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  


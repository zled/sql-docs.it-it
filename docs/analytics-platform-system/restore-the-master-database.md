---
title: Ripristinare il Database Master (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7870021a-0d89-422e-b8ea-1cc95b45c139
caps.latest.revision: "11"
ms.openlocfilehash: b82ef65734b6953c085436d5322e7bf42ef979b4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="restore-the-master-database"></a>Ripristinare il Database Master
Il **ripristino Master** pagina di Gestione configurazione SQL Server PDW consente di ripristinare il database master da un backup.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
> [!IMPORTANT]  
> Per eseguire il ripristino, SQL Server PDW necessario eliminare il database principale corrente, che contiene informazioni di sicurezza utente e il catalogo del database. È consigliabile eseguire un backup del database master corrente prima di eseguire il ripristino.  
  
## <a name="to-restore-the-master-database"></a>Per ripristinare il database master  
  
1.  Avviare Gestione configurazione. Per ulteriori informazioni, vedere [avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41; ](launch-the-configuration-manager.md).  
  
2.  Nel riquadro a sinistra di Configuration Manager, fare clic su **ripristino Master**.  
  
3.  Selezionare il backup del master da ripristinare.  
  
4.  Fare clic su **Applica**.  
  
5.  Per eseguire il ripristino, SQL Server PDW arresteranno tutti i servizi di dispositivo e disconnettere tutti gli utenti. Dopo il completamento del ripristino, SQL Server PDW verrà riavviare i servizi di dispositivo.  
  
![DWConfig ripristino master PDW strumento](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  

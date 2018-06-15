---
title: Ripristinare il database master - Analitica Platform System | Documenti Microsoft
description: Ripristinare il database master nel sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538401"
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Ripristinare il database master nel sistema della piattaforma Analitica
Il **ripristino Master** pagina di Gestione configurazione SQL Server PDW consente di ripristinare il database master da un backup.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
> [!IMPORTANT]  
> Per eseguire il ripristino, SQL Server PDW necessario eliminare il database principale corrente, che contiene informazioni di sicurezza utente e il catalogo del database. È consigliabile eseguire un backup del database master corrente prima di eseguire il ripristino.  
  
## <a name="to-restore-the-master-database"></a>Per ripristinare il database master  
  
1.  Avviare Gestione configurazione. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro a sinistra di Configuration Manager, fare clic su **ripristino Master**.  
  
3.  Selezionare il backup del master da ripristinare.  
  
4.  Fare clic su **Applica**.  
  
5.  Per eseguire il ripristino, SQL Server PDW arresteranno tutti i servizi di dispositivo e disconnettere tutti gli utenti. Dopo il completamento del ripristino, SQL Server PDW verrà riavviare i servizi di dispositivo.  
  
![DWConfig ripristino master PDW strumento](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  

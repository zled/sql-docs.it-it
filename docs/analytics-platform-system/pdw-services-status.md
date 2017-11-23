---
title: Stato servizi PDW (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fc9bee2-c372-4c4a-956c-fb54215d8918
caps.latest.revision: "14"
ms.openlocfilehash: 252a18f85d86129aa9f1916a224048b7e4b03f30
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="pdw-services-status"></a>Stato servizi PDW
Parallel Data Warehouse **stato del servizio** pagina nel gestore di configurazione sistema Microsoft Analitica piattaforma Mostra lo stato corrente di tutti i servizi di SQL Server PDW e offre la possibilità di arrestare e avviare i servizi PDW. Questo è l'unico metodo supportato per l'avvio e arresto dei servizi PDW. Si noti che i singoli componenti o servizi possono essere avviati in modo indipendente.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Per avviare o arrestare i servizi di dispositivo  
  
1.  Per avviare i servizi di dispositivo, fare clic su **dispositivo avviare**.  
  
2.  Per arrestare i servizi di dispositivo, fare clic su **arrestare accessorio**.  
  
Non è necessario fare clic su **applica** durante l'avvio e arresto dei servizi di dispositivo utilizzando **dispositivo avviare** e **arrestare accessorio**.  
  
![Servizi PDW strumento DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> L'arresto dell'area PDW interrompe anche l'agente PDW (sqldwagent) nei nodi dell'area di HDInsight. L'area di HDInsight è funziona, tuttavia, il monitoraggio dello stato non sarà disponibile. Per l'agente PDW è necessario il nodo controllo PDW per segnalare il monitoraggio dello stato.  
  
## <a name="see-also"></a>Vedere anche  
[Accendere il dispositivo di punti di accesso o disattivare &#40; Sistema della piattaforma Analitica &#41;](power-the-aps-appliance-on-or-off.md)  
  

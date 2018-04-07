---
title: Stato servizi PDW (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fc9bee2-c372-4c4a-956c-fb54215d8918
caps.latest.revision: 14
ms.openlocfilehash: 727adf27c5118130682d8d63eb120c67380ac20d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
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
[Risparmio energia accessorio APS o disattivare &#40;Analitica Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  

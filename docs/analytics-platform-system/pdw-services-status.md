---
title: -Stato di servizi PDW Analitica Platform System | Documenti Microsoft
description: Parallel Data Warehouse (PDW) dello stato dei servizi di sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e2252bb821f9522515f1625b0fc118323cb50d1f
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Lo stato dei servizi Parallel Data Warehouse per Analitica Platform System
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
  

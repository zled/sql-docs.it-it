---
title: Configurazione del fuso orario dispositivo (Analitica piattaforma sistema)
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
ms.assetid: cea9eeb9-fe05-4e65-b229-539de02ab20a
caps.latest.revision: 18
ms.openlocfilehash: cb03dd9b766c92e92b329f1e0c9daedb7cd56703
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="appliance-time-zone-configuration"></a>Configurazione del fuso orario dispositivo
Il **fuso orario** pagina consente di impostare il fuso orario per tutti i nodi nel dispositivo di SQL Server PDW.  
  
## <a name="to-set-the-time-zone"></a>Per impostare il fuso orario  
  
1.  Avviare Gestione configurazione. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Arrestare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Vedere [PDW stato del servizio &#40;Analitica Platform System&#41; ](pdw-services-status.md) per istruzioni.  
  
3.  Nel riquadro a sinistra di Configuration Manager, fare clic su **fuso orario**. Selezionare il fuso orario desiderato dal **fuso orario** dal menu a discesa. A seconda del percorso, è possibile anche scegliere di selezionare la casella accanto a **imposta automaticamente l'ora legale**.  
  
4.  Fare clic su **applica** per salvare le modifiche.  
  
5.  Riavviare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Se inoltre si intende modificare i privilegi, è possibile farlo prima di riavviare il dispositivo.  
  
![DWConfig Appliance Time](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
  

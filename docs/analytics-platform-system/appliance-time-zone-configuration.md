---
title: Configurazione del fuso orario dispositivo (Analitica piattaforma sistema)
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
ms.assetid: cea9eeb9-fe05-4e65-b229-539de02ab20a
caps.latest.revision: "18"
ms.openlocfilehash: 05cf2811dad14a6a7d53752893f363b061b86843
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="appliance-time-zone-configuration"></a>Configurazione del fuso orario dispositivo
Il **fuso orario** pagina consente di impostare il fuso orario per tutti i nodi nel dispositivo di SQL Server PDW.  
  
## <a name="to-set-the-time-zone"></a>Per impostare il fuso orario  
  
1.  Avviare Gestione configurazione. Per ulteriori informazioni, vedere [avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41; ](launch-the-configuration-manager.md).  
  
2.  Arrestare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Vedere [PDW servizi stato &#40; Sistema della piattaforma Analitica &#41; ](pdw-services-status.md) per le istruzioni.  
  
3.  Nel riquadro a sinistra di Configuration Manager, fare clic su **fuso orario**. Selezionare il fuso orario desiderato dal **fuso orario** dal menu a discesa. A seconda del percorso, è possibile anche scegliere di selezionare la casella accanto a **imposta automaticamente l'ora legale**.  
  
4.  Fare clic su **applica** per salvare le modifiche.  
  
5.  Riavviare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Se inoltre si intende modificare i privilegi, è possibile farlo prima di riavviare il dispositivo.  
  
![Ora dello strumento DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41;](launch-the-configuration-manager.md)  
  

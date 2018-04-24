---
title: Configurare il fuso orario - Analitica Platform System | Documenti Microsoft
description: La pagina di fuso orario consente di impostare il fuso orario per tutti i nodi nel dispositivo di sistema della piattaforma Analitica (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6a17ef4e77f9703a285f1e232077582e4441f293
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>Configurazione del fuso orario accessorio - Analitica Platform System
Il **fuso orario** pagina consente di impostare il fuso orario per tutti i nodi nel dispositivo di sistema della piattaforma Analitica (AP).  
  
## <a name="to-set-the-time-zone"></a>Per impostare il fuso orario  
  
1.  Avviare Gestione configurazione. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Arrestare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Vedere [PDW stato del servizio &#40;Analitica Platform System&#41; ](pdw-services-status.md) per istruzioni.  
  
3.  Nel riquadro a sinistra di Configuration Manager, fare clic su **fuso orario**. Selezionare il fuso orario desiderato dal **fuso orario** dal menu a discesa. A seconda del percorso, è possibile anche scegliere di selezionare la casella accanto a **imposta automaticamente l'ora legale**.  
  
4.  Fare clic su **applica** per salvare le modifiche.  
  
5.  Riavviare i servizi di dispositivo utilizzando il **stato del servizio** pagina in Configuration Manager. Se inoltre si intende modificare i privilegi, è possibile farlo prima di riavviare il dispositivo.  
  
![DWConfig Appliance Time](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
  

---
title: Monitoraggio con SCOM - Analitica Platform System | Documenti Microsoft
description: Utilizzare System Center Operations Manager (SCOM) per monitorare l'accessorio Analitica Platform System (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2b26462ab37cf7d63960ff7db6e20c57e8290bb
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538981"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Monitoraggio con System Center Operations Manager - Analitica Platform System
Utilizzare System Center Operations Manager (SCOM) per monitorare l'accessorio Analitica Platform System (AP).
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisiti  
  
1.  System Center Operations Manager 2007 R2, 2012 o 2012 SP1 deve essere installato e in esecuzione.  
  
2.  È necessario installare SQL Server 2008 R2 Native Client o SQL Server 2012 Native Client.  
  
3.  I management pack per monitorare SQL Server PDW e HDInsight deve essere installato, importato e configurato. Utilizzare i seguenti articoli per le istruzioni per eseguire queste attività.  
  
    -   [Installare i Management Pack SCOM &#40;Analitica Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [Importare il Management Pack SCOM per PDW &#40;Analitica Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Configurare SCOM per il monitoraggio di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Per monitorare SQL Server PDW con SCOM  
Dopo aver configurato i Management Pack di SCOM, fare clic su Monitoraggio riquadro di SCOM e drill-down **dispositivo di SQL Server** e quindi **Microsoft SQL Server Parallel Data Warehouse**. Di sotto di Microsoft SQL Server Parallel Data Warehouse, sono disponibili quattro opzioni: avvisi, dispositivi, diagramma dello strumento e i nodi.  
  
### <a name="alerts"></a>Avvisi  
Gli avvisi sono in cui è possibile trovare gli avvisi correnti per la gestione.  
  
![Gli avvisi](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Strumenti  
Dispositivi sono disponibili l'attualmente individuati e monitorati SQL Server PDW Appliance nell'ambiente in uso. Se un dispositivo non vengono visualizzati qui e aver creato la connessione ODBC per tale, può essere presente un problema con l'account PDWWatcher. Se vengono visualizzati come "Non monitorato", potrebbe esserci un problema con il proprio account PDWMonitor. Essere paziente poiché SCOM non apporta modifiche in tempo reale, ma vengono periodicamente verificate le nuovi accessori monitorare e invia periodicamente le query con dispositivi per il monitoraggio.  
  
![Accessori](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Diagramma strumenti  
La pagina di diagramma di accessori è dove è possibile ottenere un aspetto dello stato del dispositivo con una visualizzazione albero:  
  
![Diagramma strumenti](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Nodi  
Infine, la visualizzazione di nodi consente di visualizzare l'integrità del dispositivo tramite ogni nodo:  
  
![I nodi](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Avvisi della Console di amministrazione di informazioni sui &#40;Analitica Platform System&#41;](understanding-admin-console-alerts.md)  
  

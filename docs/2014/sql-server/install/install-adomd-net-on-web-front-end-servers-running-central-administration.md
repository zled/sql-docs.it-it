---
title: Installare ADOMD.NET in server front-end Web in esecuzione Amministrazione centrale | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: ccedd48fcebab07eeb7b27821917b684d98a11d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067112"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Installare ADOMD.NET in server front-end Web in cui viene eseguita Amministrazione centrale
  Se si installa PowerPivot per SharePoint in una farm che dispone della topologia di Amministrazione centrale, senza Excel Services o PowerPivot per SharePoint, scaricare e installare la libreria client Microsoft ADOMD.NET se si desidera l'accesso completo ai report incorporati nel dashboard di gestione PowerPivot. Alcuni report nel dashboard utilizzano ADOMD.NET per accedere a dati interni relativi all'integrità del server e all'elaborazione query di PowerPivot nella farm.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Per SharePoint 2013, il provider è incluso nel Feature Pack di SQL Server. Per informazioni su come scaricare sppowerpivot. msi, vedere [Microsoft SQL Server 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Scaricare e installare la libreria client  
  
1.  Nel [pagina Feature Pack di SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296473), trovare Microsoft ADOMD.NET.  
  
2.  Scaricare il pacchetto per x64 del programma di installazione `SQL_AS_ADOMD.msi`.  
  
3.  Eseguire il file con estensione msi per installare la libreria.  
  
4.  Reimpostare IIS dopo aver completato l'installazione. Aprire un prompt dei comandi amministrativo e digitare **IISRESET**.  
  
### <a name="verify-installation"></a>Verificare l'installazione  
  
1.  Spostarsi su Windows\Assembly.  
  
2.  Fare doppio clic su Microsoft.AnalysisServices.AdomdClient e selezionare **proprietà**.  
  
3.  Fare clic su **Versione**.  
  
4.  Verificare che la versione includa 12.00.<numero. \<numero di build > e che la descrizione sia analysisservice.  
  
## <a name="see-also"></a>Vedere anche  
 [PowerPivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
---
title: Log degli errori di SQL Server (Gruppi di disponibilità Always On (SQL Server) | Microsoft Docs
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
caps.latest.revision: 4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d776c9447925c494df3245efb487409d272b9d99
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>Log degli errori di SQL Server (Gruppi di disponibilità Always On)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il log degli errori di SQL Server segnala gli eventi che interessano Gruppi di disponibilità Always On, ad esempio:  
  
-   Comunicazione con il cluster WSFC (Windows Server Failover Clustering)  
  
-   Transizioni di stato delle replica di disponibilità  
  
-   Transizioni di stato dei database di disponibilità  
  
-   Stato di connettività dei database di disponibilità tra repliche primarie e secondarie  
  
-   Stati degli endpoint del gruppo di disponibilità  
  
-   Stati dei listener del gruppo di disponibilità  
  
-   Stato lease tra la DLL risorse SQL Server (in esecuzione nel cluster WSFC) e l'istanza di SQL Server (per altre informazioni, vedere [How It Works: SQL Server Always On lease timeout](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx) (Funzionamento: timeout lease di SQL Server Always On)  
  
-   Eventi di errore nel gruppo di disponibilità  


Esaminare il log degli errori di SQL Server rivedendo i sintomi seguenti:  

-   Impossibile accedere ai database di disponibilità  
  
-   Failover imprevisto del gruppo di disponibilità  
  
-   Gruppo di disponibilità inaspettatamente con lo stato Risoluzione in corso  
  
-   Gruppo di disponibilità in uno stato indeterminato  
  
Per altre informazioni, vedere [View the SQL Server error log &#40;SQL Server Management Studio&#41;](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md) (Visualizzare il log degli errori di SQL Server &#40;SQL Server Management Studio&#41)  
  
  
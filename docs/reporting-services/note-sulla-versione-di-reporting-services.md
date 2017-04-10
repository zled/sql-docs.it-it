---
title: "Technical Preview dei report di Power BI in SSRS - Note sulla versione | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f20d7-a9f9-47e3-8dc3-c544a14457e0
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Note sulla versione di Reporting Services
 ||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  Technical Preview di gennaio 2017 dei report di Power BI in SQL Server Reporting Services|

Questo argomento descrive le limitazioni e i problemi relativi alla Technical Preview dei report di Power BI in SQL Server Reporting Services.

- Per informazioni sulle novità introdotte in questa versione, vedere [Novità di Reporting Services](../reporting-services/novità-di-sql-server-reporting-services-ssrs.md).

 **Per provarlo:**    
   -   [![Scaricare dall'Area Download Microsoft](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?linkid=839351)  Scaricare la Technical Preview dei report di Power BI in SQL Server Reporting Services e Power BI Desktop (SQL Server Reporting Services) dall'**[Area download Microsoft](https://go.microsoft.com/fwlink/?linkid=839351)**.


## <a name="january--2017"></a>Gennaio 2017

### <a name="report-server"></a>Server di report

- È ora incluso il supporto per HTTPS. Questo supporto non era disponibile nella Technical Preview VM rilasciata in ottobre 2016. Per altre informazioni, vedere [Configurare connessioni SSL in un server di report in modalità nativa](../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).
   - HTTPS è necessario per usare il componente aggiuntivo del visualizzatore Web di PowerPoint ed esporre i report di Power BI in tale visualizzatore.
- È ora incluso il supporto per la scalabilità orizzontale. Questo supporto non era disponibile nella Technical Preview VM rilasciata in ottobre 2016. Per altre informazioni, vedere [Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa](../reporting-services/install-windows/configure a native mode report server scale-out deployment.md).

### <a name="power-bi-reports"></a>Report di Power BI

- Per funzionare con SQL Server Reporting Services, i report di Power BI devono essere creati con Power BI Desktop (SQL Server Reporting Services). È possibile scaricare Power BI Desktop (SQL Server Reporting Services) da Evaluation Center.
- I report di Power BI supportano solo le connessioni dinamiche ad Analysis Services (tabulari o multidimensionali).
- Non è previsto il supporto per oggetti visivi personalizzati.
- Non è previsto il supporto per oggetti visivi R.
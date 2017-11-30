---
title: Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: "32"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f52059e27008b5a29bd14f95f6a20d1a1d64d207
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL
  È possibile eseguire il rendering di un report in base allo snapshot della cronologia del report fornendo il parametro *rs:Snapshot* e impostandone il valore su un ID di snapshot valido. Il valore di questo parametro è nel formato AAAA-MM-GGTHH:MM:SS, in base allo standard ISO (International Organization for Standardization) 8601.  
  
 Se si omette questo parametro, il rendering del report viene eseguito in base alle impostazioni dell'opzione di esecuzione del report e gestione della cache del server di report. Per altre informazioni sull'esecuzione di report, vedere [Impostare proprietà di elaborazione dei report](../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un URL che consente di recuperare uno snapshot della cronologia del report:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
  
  

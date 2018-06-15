---
title: Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 54c58684f22f607fe6f951ce0404f327b2d92ce7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33018488"
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
  
  

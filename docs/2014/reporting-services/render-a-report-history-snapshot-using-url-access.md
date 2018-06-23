---
title: Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
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
manager: mblythe
ms.openlocfilehash: 29ff943923807b88db27bd9c8c6a1cc8430f96a3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155713"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Eseguire il rendering degli snapshot della cronologia dei report tramite l'accesso con URL
  È possibile eseguire il rendering di un report in base allo snapshot della cronologia del report fornendo il parametro *rs:Snapshot* e impostandone il valore su un ID di snapshot valido. Il valore di questo parametro è nel formato AAAA-MM-GGTHH:MM:SS, in base allo standard ISO (International Organization for Standardization) 8601.  
  
 Se si omette questo parametro, il rendering del report viene eseguito in base alle impostazioni dell'opzione di esecuzione del report e gestione della cache del server di report. Per ulteriori informazioni sull'esecuzione dei report, vedere [imposta proprietà di elaborazione Report](report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un URL che consente di recuperare uno snapshot della cronologia del report:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso con URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](url-access-parameter-reference.md)  
  
  
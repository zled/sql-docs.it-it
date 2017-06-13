---
title: Ricerca di un Report con accesso tramite URL | Documenti Microsoft
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
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 39ec7f9885cff6bcfcbf65e0448f3e8e837bc8a6
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="search-a-report-using-url-access"></a>Cercare un report tramite l'accesso con URL
  È possibile cercare in un report del testo specifico utilizzando l'accesso tramite URL. Per eseguire una ricerca in un report, impostare il valore del parametro *rc:FindString* nell'URL affinché corrisponda al testo da cercare. Inoltre, usare i parametri *rc:StartFind* e *rc:EndFind* per restringere la ricerca alle pagine specifiche all'interno del report.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di accesso tramite URL seguente viene cercata la prima occorrenza del testo "Mountain-400" nel report di esempio Product Catalog a partire da pagina uno fino a pagina cinque:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
  
  

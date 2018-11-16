---
title: Cercare un report tramite l'accesso con URL | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a63f4c1c1ad925ee57def853c76f71ec52f9cb58
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813194"
---
# <a name="search-a-report-using-url-access"></a>Cercare un report tramite l'accesso con URL
  È possibile cercare in un report del testo specifico utilizzando l'accesso tramite URL. Per eseguire una ricerca in un report, impostare il valore del parametro *rc:FindString* nell'URL affinché corrisponda al testo da cercare. Inoltre, usare i parametri *rc:StartFind* e *rc:EndFind* per restringere la ricerca alle pagine specifiche all'interno del report.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di accesso tramite URL seguente viene cercata la prima occorrenza del testo "Mountain-400" nel report di esempio Product Catalog a partire da pagina uno fino a pagina cinque:  
  
```  
https://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
  
  

---
title: Novità&#39;s nuovo (Integration Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c7d37fb3c1d2cd1dcafecc012fbe83e1864e50ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055942"
---
# <a name="what39s-new-integration-services"></a>Novità&#39;s nuovo (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è invariato dalla versione precedente.  
  
 Per informazioni su altri [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] prodotti e tecnologie, vedere [novità in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Per ulteriori informazioni sulle modifiche correlate a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, vedere [novità in Analysis Services e Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Output di convalida XML avanzato in Attività XML  
 Convalidare documenti XML e ottenere output avanzato degli errori abilitando la `ValidationDetails` proprietà dell'attività XML. Prima di `ValidationDetails` proprietà era disponibile, la convalida XML dall'attività XML restituiva solo un risultato true o false, senza informazioni sugli errori o le relative posizioni sulle. A questo punto, quando si imposta `ValidationDetails` su true, l'output file contiene informazioni dettagliate su ogni errore, inclusi il numero di riga e la posizione. È possibile usare questa informazione per comprendere, individuare e risolvere gli errori nei documenti XML. Per ulteriori informazioni, vedere [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] introdotto il `ValidationDetails` proprietà [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Questa nuova proprietà non è stata annunciata o documentata in quel momento. Il `ValidationDetails` proprietà è disponibile anche in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] e in SQL Server 2016.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
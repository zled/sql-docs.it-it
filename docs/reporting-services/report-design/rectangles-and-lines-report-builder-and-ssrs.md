---
title: Rettangoli e linee (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bc6c8bc8ddf4e23afe15c533a49a30c96702294c
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a>Rettangoli e linee (Generatore report e SSRS)
  È possibile usare rettangoli e linee per creare effetti visivi all'interno di un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . Le proprietà di visualizzazione per questi elementi del report si impostano dalla sezione Bordo della scheda Home mentre per le altre proprietà si usa il riquadro Proprietà. A un rettangolo è possibile aggiungere caratteristiche come un colore di sfondo o un'immagine, una descrizione comando o un segnalibro.  
  
##  <a name="RectanglesLinesReportParts"></a> Rettangoli e linee come parti del report  
 È possibile pubblicare rettangoli con gli elementi in essi contenuti separatamente dal report come parti del report. Le parti del report sono elementi autonomi del report archiviati sul server di report e possono essere incluse in altri report.  
  
 Non è possibile pubblicare gli elementi del report all'interno di un rettangolo come parti del report. Quando gli utenti aggiungono il rettangolo a un report, ottengono il rettangolo e gli elementi in esso contenuti.  Altre informazioni su [Parti del report](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md).  
  
##  <a name="RectangleAsContainer"></a> Utilizzo di un rettangolo come contenitore  
 È possibile utilizzare un rettangolo come contenitore per altri elementi. Quando si sposta il rettangolo, vengono spostati anche gli elementi contenuti all'interno del rettangolo. Un elemento all'interno del rettangolo consente di visualizzare il nome del rettangolo nella proprietà **Parent**. Per altre informazioni sull'uso di un rettangolo come contenitore, vedere [Aggiungere un rettangolo o un contenitore &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md) e [Visualizzare dati identici in una matrice e in un grafico &#40;Generatore report&#41;](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  Un rettangolo è solo un contenitore di elementi che in esso vengono creati o trascinati. Se si disegna un rettangolo intorno a un elemento esistente nell'area di progettazione, il rettangolo non agirà da contenitore. non sarà elencato nella proprietà Parent dell'elemento.  
  
 Quando si utilizzano rettangoli per contenere elementi del report, occorre tenere in considerazione il modo in cui gli elementi verranno modificati nel loro insieme durante il rendering del report. Gli elementi del report che contengono righe ripetute di dati, ad esempio le tabelle, possono espandersi per adattarsi ai dati restituiti da una query modificando di conseguenza il posizionamento degli altri elementi all'interno del rettangolo. Una tabella sposterà gli elementi verso il basso se sono posizionati al di sotto dell'area dati. Per ancorare un elemento, è possibile posizionarlo all'interno di un rettangolo il cui bordo superiore si trovi più in alto rispetto al bordo inferiore della tabella. Per altre informazioni, vedere [Tipi di rendering  &#40;Generatore report e SSRS &#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
##  <a name="ReportBorder"></a> Aggiunta di un bordo al report  
 È possibile aggiungere un bordo a un report aggiungendo bordi alle intestazioni, ai piè di pagina e al corpo del report, senza inserire righe o rettangoli. Per altre informazioni, vedere [Aggiungere un bordo a un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-border-to-a-report-report-builder-and-ssrs.md).  
  
##  <a name="HowTo"></a> Procedure  
 [Aggiungere un bordo a un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [Aggiungere un rettangolo o un contenitore &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [Aggiungere e modificare una linea &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere un rettangolo o un contenitore &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  

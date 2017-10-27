---
title: "Il collegamento di più aree dati allo stesso set di dati (Generatore Report e SSRS) | Documenti Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90c94a91-8fb2-42cb-b998-563691f30d2d
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 32d055510fd5b04676f2c8fc715e6b7ea132eda9
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---

# <a name="linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs"></a>Collegamento di più aree dati allo stesso set di dati (Generatore report e SSRS)

È possibile aggiungere più aree dati a un report impaginato di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per fornire visualizzazioni diverse dei dati dello stesso set di dati del report. Può ad esempio verificarsi l'esigenza di visualizzare i dati sia in una tabella che visivamente in un grafico. A tale scopo, è necessario utilizzare espressioni e ambiti identici per le espressioni di filtro, le espressioni di ordinamento e le espressioni di raggruppamento appropriate.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Per utilizzare un grafico e una tabella o una matrice per visualizzare gli stessi dati, può risultare utile avere un'idea delle analogie tra una tabella e i grafici con forme e tra una matrice e i grafici ad area, a barre e gli istogrammi. Una tabella con un solo gruppo di righe può essere visualizzata facilmente come grafico a torta. Se si aggiungono più gruppi di righe, è possibile scegliere tipi diversi di grafici per visualizzare in modo più efficace i gruppi nidificati. Aggiungendo gruppi di righe nidificati a un grafico a torta si aumenta il numero di sezioni della torta. È necessario valutare se il numero di istanze di gruppo per la combinazione di gruppo padre e gruppo figlio è troppo elevato per essere visualizzato in un solo grafico a torta. Nel caso di più valori di gruppo visualizzati come piccole sezioni in un grafico a torta, è possibile impostare una proprietà in base alla quale tutti i valori al di sotto di una determinata soglia vengano visualizzati come un'unica sezione della torta. Per ulteriori informazioni, vedere [raccogliere piccole sezioni in un grafico a torta](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md).  
  
 Una tabella con più gruppi di righe può essere mostrata come un istogramma con più gruppi di categorie. Per ulteriori informazioni, vedere [visualizzare gli stessi dati in una matrice e un grafico](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md). Per un esempio di una tabella e un grafico che presentano visualizzazioni diverse dello stesso set di dati del report, fare riferimento al report Product Line Sales negli esempi di report di AdventureWorks. Poiché sia la tabella che il grafico sono collegati allo stesso set di dati in questo report, quando si fa clic sul pulsante di ordinamento interattivo relativo al nome del dipendente nella tabella Top Employees, anche nel grafico Top Employees viene mostrato automaticamente il nuovo ordinamento. Per ulteriori informazioni sul download di questo report di esempio e ad altri utenti, vedere [report di Generatore Report e progettazione Report di esempio](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
 Il modo migliore per visualizzare una matrice con più gruppi di righe e colonne è utilizzare un grafico ad area, a barre o un istogramma che contenga sia i gruppi di categorie che di serie. Utilizzare le stesse espressioni di raggruppamento per i gruppi di colonne della matrice e i gruppi di categorie del grafico e le stesse espressioni di raggruppamento per gruppi di righe della matrice e i gruppi di serie del grafico. È necessario ricordare che il numero di istanze di gruppo influisce sulla leggibilità del grafico. È possibile definire i gruppi in base ai valori di intervallo per ridurre il numero di istanze di gruppo di un report. Per ulteriori informazioni, vedere [esempi di espressione di raggruppamento](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md).  
  
## <a name="next-steps"></a>Passaggi successivi

[Grafici](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Tabelle, matrici ed elenchi](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
[Aree dati nidificate](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)


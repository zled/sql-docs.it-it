---
title: Allineamento dei dati in un grafico in una tabella o matrice (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d64ebc0ee2345088419e44ab819c0d94d26274a8
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Allineare i dati in un grafico di una tabella o matrice (Generatore report e SSRS)
  I grafici sparkline e le barre dei dati sono grafici semplici, di piccole dimensioni, contenenti numerose informazioni poco dettagliate. In un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , quando si seleziona questa opzione, i valori presenti nei grafici sparkline e nelle barre dei dati vengono allineati nelle diverse celle della tabella o della matrice, anche se mancano dei valori nei dati su cui si basano.  
  
 ![rs_SparklineAlignData](../../reporting-services/report-design/media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 In questa immagine, nell'istogramma vengono mostrate le vendite giornaliere per ogni dipendente. Nei giorni in cui il dipendente non ha effettuato vendite, nel grafico viene lasciato uno spazio vuoto, mentre i giorni successivi vengono allineati orizzontalmente. I grafici vengono inoltre allineati verticalmente mettendone in relazione le diverse dimensioni. Per altre informazioni, vedere [Grafici sparkline e barre dei dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Allineare i dati in un grafico sparkline o in una barra dei dati  
  
1.  [Aggiungere grafici sparkline o barre dei dati](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md) a una tabella o a una matrice.  
  
2. Fare clic nel grafico sparkline o barra dei dati, quindi selezionare **Proprietà asse orizzontale** o **Proprietà asse verticale**.  
  
2.  Nella scheda **Opzioni asse** selezionare la casella **Align axes in** (Allinea assi in), quindi nella casella a discesa selezionare il gruppo sul quale allineare l'asse.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Grafici &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Aggiungere grafici sparkline e barre dei dati &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  

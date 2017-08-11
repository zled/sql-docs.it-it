---
title: Aggiungere codice HTML in un Report (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 17889109d30d41405b0fa13d694e29930b82a292
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a>Aggiungere il codice HTML a un report (Generatore report e SSRS)
  Utilizzando un segnaposto, è possibile importare codice HTML da un campo nel set di dati per utilizzarlo nel report. Per impostazione predefinita, un segnaposto rappresenta un testo normale e pertanto è necessario modificarne il tipo di markup in codice HTML. Per altre informazioni, vedere [Importazione di HTML in un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/importing-html-into-a-report-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a>Per aggiungere codice HTML da un campo del set di dati in una casella di testo  
  
1.  Fare clic su **Elenco** nella scheda **Inserisci**. Fare clic nell'area di progettazione, quindi trascinare il mouse per creare una casella delle dimensioni desiderate.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà set di dati** . È possibile utilizzare un set di dati condiviso o un set di dati incorporato nel report. Per altre informazioni, fare clic su [Finestra di dialogo Proprietà set di dati, Query &#40;Generatore report&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md) o [Finestra di dialogo Proprietà set di dati, Query](http://msdn.microsoft.com/library/1fa34a4b-7de0-4e92-99fa-bc28a206773f).  
  
2.  Fare clic su **Casella testo** nella scheda **Inserisci**. Fare clic nell'elenco, quindi trascinare il mouse per creare una casella con le dimensioni desiderate.  
  
3.  Trascinare un campo HTML dal set di dati nella casella di testo. Verrà creato un segnaposto per il campo.  
  
4.  Fare clic con il pulsante destro del mouse sul segnaposto, quindi scegliere **Proprietà segnaposto**.  
  
5.  Nella scheda **Generale** verificare che la casella **Valore** contenga un'espressione che restituisce il campo rilasciato nel passaggio 3.  
  
6.  Fare clic su **HTML - Interpreta tag HTML come stili**. In questo modo il campo verrà valutato come HTML.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di numeri e date &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Formattazione di linee, colori e immagini &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-lines-colors-and-images-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà segnaposto, generale &#40; Generatore report e SSRS &#41;](http://msdn.microsoft.com/library/7a867736-a3b0-4b5a-b3e5-fe7c8d7618a8)  
  
  

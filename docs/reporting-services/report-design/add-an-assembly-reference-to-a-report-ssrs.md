---
title: Aggiungere un riferimento all'Assembly a un Report (SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1bf8106435899a97572c5972721bdf3190d031a6
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Aggiungere un riferimento a un assembly in un report (SSRS)
  Quando si incorpora codice personalizzato che contiene riferimenti a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classi che non sono in <xref:System.Math> o <xref:System.Convert>, è necessario fornire un riferimento all'assembly per il report in modo che il componente elaborazione report possa risolvere i nomi. Per altre informazioni, vedere [Aggiungere codice a un report &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>Per aggiungere un riferimento a un assembly in un report  
  
1.  Nella visualizzazione **Progettazione** fare clic con il pulsante destro del mouse nell'area di progettazione all'esterno del bordo del report e scegliere **Proprietà report**.  
  
2.  Fare clic su **Riferimenti**.  
  
3.  In **Aggiungi o rimuovi assembly**fare clic su **Aggiungi** e quindi fare clic sul pulsante con i puntini di sospensione per passare all'assembly.  
  
4.  In **Aggiungi o rimuovi assembly**fare clic su **Aggiungi** e quindi digitare il nome della classe e specificare un nome di istanza da usare nel report.  
  
    > [!NOTE]  
    >  Specificare il nome di una classe e il nome di un'istanza solo per i membri basati sulle istanze. Non specificare membri statici nell'elenco **Classi**. Per altre informazioni, vedere [Riferimenti a codice personalizzato e ad assembly in espressioni in Progettazione report &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Finestra di dialogo Proprietà report, Riferimenti](http://msdn.microsoft.com/library/4639d368-9918-4bb1-9953-7a724ca78dea)  
  
  

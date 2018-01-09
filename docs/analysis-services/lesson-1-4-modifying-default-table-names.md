---
title: Modifica di nomi di tabella predefinito | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 726cab6d57171e33d30ea61d397e54f7926cf00b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-1-4---modifying-default-table-names"></a>Lezione 1-4 - modifica i nomi di tabella predefinito
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]È possibile modificare il valore di **FriendlyName** proprietà per gli oggetti nella vista origine dati per renderli più semplici da individuare e utilizzare.  
  
Nell'attività seguente si modificherà il nome descrittivo di ogni tabella nella vista origine dati rimuovendo da tali tabelle i prefissi "**Dim**" e "**Fact**". In questo modo, gli oggetti cubo e dimensione, che verranno definiti nella lezione successiva, risulteranno più semplici da individuare e utilizzare.  
  
> [!NOTE]  
> È inoltre possibile modificare i nomi descrittivi delle colonne, definire colonne calcolate e unire in join tabelle o viste della vista origine dati per semplificarne l'utilizzo.  
  
### <a name="to-modify-the-default-name-of-a-table"></a>Per modificare il nome predefinito di una tabella  
  
1.  Nel riquadro **Tabelle** di **Progettazione vista origine dati**fare clic con il pulsante destro del mouse sulla tabella **FactInternetSales** e quindi scegliere **Proprietà**.  
  
2.  Se la finestra Proprietà non è visualizzata sul lato destro della finestra di Microsoft Visual Studio, fare clic sul pulsante **Nascondi automaticamente** sulla barra del titolo della finestra Proprietà in modo che la finestra rimanga visibile.  
  
    Se la finestra Proprietà rimane aperta è più facile modificare le proprietà di ogni tabella della vista origine dati. Se la finestra non viene tenuta aperta usando il pulsante **Nascondi automaticamente** , si chiuderà quando si fa clic su un altro oggetto nel riquadro **Diagramma** .  
  
3.  Modificare la proprietà **FriendlyName** dell'oggetto **FactInternetSales** in ***InternetSales***.  
  
    La modifica viene applicata quando si fa clic in un punto diverso dalla cella della proprietà **FriendlyName** . Nella lezione successiva si definirà un gruppo di misure basato su questa tabella dei fatti. Il nome della tabella dei fatti sarà InternetSales anziché FactInternetSales a causa della modifica apportata in questa lezione.  
  
4.  Fare clic su **DimProduct** nel riquadro **Tabelle** . Nella finestra Proprietà modificare la proprietà **FriendlyName** in ***Product***.  
  
5.  Modificare la proprietà **FriendlyName** delle tabelle rimanenti nella vista origine dati allo stesso modo per rimuovere il prefisso "**Dim**".  
  
6.  Al termine fare di nuovo clic sul pulsante **Nascondi automaticamente** per nascondere la finestra Proprietà.  
  
7.  Scegliere **Salva tutti** dal menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]File **o sulla barra degli strumenti di** per salvare le modifiche apportate fino a questo punto al progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Se si desidera, è possibile arrestare l'esercitazione e riprenderla in seguito.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Definizione e distribuzione di un cubo](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>Vedere anche  
[Viste origine dati in modelli multidimensionali](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
[Modificare le proprietà in una vista origine dati &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
  

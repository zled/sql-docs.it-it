---
title: Modifica delle misure | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91de9fa781025b79f8aa47ff4e75067fe1045e88
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017058"
---
# <a name="lesson-3-1---modifying-measures"></a>Lezione 3-1-modifica delle misure
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

È possibile usare la proprietà **FormatString** per definire impostazioni di formattazione che controllano la modalità di visualizzazione delle misure agli utenti. In questa attività vengono impostate le proprietà di formattazione per le misure di valuta e di percentuale nel cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
### <a name="to-modify-the-measures-of-the-cube"></a>Per modificare le misure del cubo  
  
1.  Passare alla scheda **Struttura cubo** di Progettazione cubi per il cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial, espandere il gruppo di misure **Internet Sales** nel riquadro **Misure** , fare clic con il pulsante destro del mouse su **Order Quantity**, quindi scegliere **Proprietà**.  
  
2.  Nella finestra Proprietà fare clic sull'icona a forma di puntina da disegno **Nascondi automaticamente** per mantenere aperta la finestra Proprietà.  
  
    Con la finestra Proprietà aperta risulta più agevole modificare le proprietà per diversi elementi nel cubo.  
  
3.  Nella finestra Proprietà fare clic sull'elenco **FormatString** e quindi digitare **#,#**.  
  
4.  Sulla barra degli strumenti della scheda **Struttura cubo** fare clic sull'icona **Mostra griglie delle misure** a sinistra.  
  
    Nella visualizzazione griglia è possibile selezionare più misure contemporaneamente.  
  
5.  Selezionare le misure seguenti. Per selezionare più misure, fare clic su ognuna di esse tenendo premuto CTRL:  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  Nell'elenco **FormatString** della finestra Proprietà selezionare **Currency**.  
  
7.  Nell'elenco a discesa nella parte superiore della finestra Proprietà sotto la barra del titolo selezionare la misura **Unit Price Discount Pct**, quindi selezionare **Percent** nell'elenco **FormatString** .  
  
8.  Nella finestra Proprietà modificare la proprietà **Name** della misura **Unit Price Discount Pct** in **Unit Price Discount Percentage**.  
  
9. Nel riquadro **Misure** fare clic su **Tax Amt** e modificare il nome della misura in **Tax Amount**.  
  
10. Nella finestra Proprietà fare clic sull'icona **Nascondi automaticamente** per nascondere la finestra Proprietà, quindi fare clic su **Mostra albero delle misure** sulla barra degli strumenti della scheda **Struttura cubo** .  
  
11. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Modifica della dimensione Customer](../analysis-services/lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>Vedere anche  
[Definire le dimensioni del database](../analysis-services/multidimensional-models/define-database-dimensions.md)  
[Configurare le proprietà delle misure](../analysis-services/multidimensional-models/configure-measure-properties.md)  
  
  
  

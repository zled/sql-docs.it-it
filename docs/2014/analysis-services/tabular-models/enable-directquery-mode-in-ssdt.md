---
title: Abilitare la modalità DirectQuery (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93b95dc39c0efb088003af9d5fb8b68cfce11ce9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310411"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>Abilitare la modalità DirectQuery (SSAS tabulare)
  Per creare un modello in modalità DirectQuery, è innanzitutto necessario modificare l'ambiente di progettazione in modo che supporti l'utente della modalità DirectQuery. Quando si esegue questa operazione, vengono anche eseguite le operazioni seguenti:  
  
-   Abilitazione dell'utilizzo delle proprietà di distribuzione DirectQuery.  
  
-   Modifica del database dell'area di lavoro affinché venga eseguito in una modalità ibrida che utilizza la cache per la progettazione. Quando si distribuisce il modello, la modalità verrà nuovamente impostata sul valore specificato nelle proprietà di distribuzione del progetto.  
  
-   Disabilitazione delle caratteristiche di progettazione incompatibili con la modalità DirectQuery.  
  
-   Convalida del modello esistente.  
  
 Questa procedura descrive come abilitare la modalità DirectQuery nella finestra di progettazione.  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>Per abilitare l'utilizzo di DirectQuery in un modello  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], aprire il file della soluzione.  
  
2.  In Esplora oggetti fare doppio clic sul file Model.bim.  
  
3.  Nel riquadro **Proprietà** impostare la proprietà **DirectQueryMode**su **Attivato**.  
  
4.  Se sono presenti errori, in Visual Studio, aprire il **elenco errori** e risolvere eventuali problemi che impedirebbero di impostare la modalità DirectQuery per il modello.  
  
## <a name="see-also"></a>Vedere anche  
 [La modalità DirectQuery &#40;tabulare di SSAS&#41;](directquery-mode-ssas-tabular.md)  
  
  

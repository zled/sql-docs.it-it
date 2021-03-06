---
title: Definire le assegnazioni e altri comandi Script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c03a6b532dbbc5b243119d20e14856a232180c6a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196741"
---
# <a name="define-assignments-and-other-script-commands"></a>Definire le assegnazioni e altri comandi script
  Per creare uno script vuoto, nella scheda **Calcoli** di Progettazione cubi fare clic sull'icona **Nuovo comando script** sulla barra degli strumenti. Quando si crea un nuovo script, quest'ultimo viene inizialmente visualizzato con un titolo vuoto nel riquadro **Libreria script** della scheda Calcoli. I caratteri digitati nel riquadro Espressioni calcoli verranno visualizzati come nome dell'elemento in **Libreria script**. Nella prima riga è pertanto opportuno digitare un nome con commenti, in modo da identificare più agevolmente lo script nel riquadro **Libreria script** . Per altre informazioni, vedere [Introduction to MDX Scripting in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892)(Introduzione alla creazione di script MDX in Microsoft SQL Server 2005). Per altre informazioni su problemi di prestazioni relativi a query e calcoli MDX, vedere la sezione relativa alla scrittura di espressioni MDX efficienti nella [Guida alle prestazioni di SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
> [!IMPORTANT]  
>  Quando si passa inizialmente alla scheda **Calcoli** di Progettazione cubi, nel riquadro **Libreria script** è presente un unico script con un comando CALCULATE. Il comando CALCULATE controlla l'aggregazione delle celle del cubo ed è consigliabile modificarlo solo se si desidera specificare manualmente la modalità di aggregazione delle celle del cubo.  
  
 È possibile utilizzare il riquadro Espressioni calcoli per compilare un'espressione nella sintassi MDX (Multidimensional Expression). Durante il processo di compilazione dell'espressione, è possibile trascinare o copiare componenti, funzioni e modelli del cubo dal riquadro **Strumenti di calcolo** nel riquadro Espressioni di calcolo. In questo modo lo script per l'elemento viene aggiunto al riquadro Espressioni di calcolo nella posizione in cui si rilascia o incolla l'elemento. Sostituire gli argomenti e i rispettivi delimitatori (« e ») con i valori appropriati.  
  
> [!IMPORTANT]  
>  Quando si scrive un'espressione contenente più istruzioni utilizzando il riquadro Espressioni di calcolo, verificare che tutte le righe dello script MDX ad eccezione dell'ultima terminino con un punto e virgola (;). I calcoli vengono concatenati in un singolo script MDX e ad ogni script viene aggiunto un punto e virgola in modo da garantire la corretta compilazione dello script MDX. Se si aggiunge un punto e virgola all'ultima riga dello script nel riquadro Espressioni di calcoli, il cubo verrà compilato e distribuito in modo corretto, ma non sarà possibile eseguirvi query.  
  
## <a name="see-also"></a>Vedere anche  
 [Calcoli nei modelli multidimensionali](calculations-in-multidimensional-models.md)  
  
  

---
title: Converti in finestra di dialogo modello di distribuzione di pacchetto | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 69d64b35f39c86b9070df9c9fcfacfcf9a7d68f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069430"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>Finestra di dialogo Converti in modello di distribuzione di pacchetti
  Con il comando **Converti nel modello di distribuzione del pacchetto** è possibile convertire un pacchetto nel modello di distribuzione del pacchetto dopo aver verificato la compatibilità del progetto e di ogni relativo pacchetto con questo modello. Se in un pacchetto vengono utilizzate funzionalità univoche per il modello di distribuzione del progetto, ad esempio parametri, il pacchetto non può essere convertito.  
  
## <a name="task-list"></a>Elenco attività  
 Per la conversione di un pacchetto nel modello di distribuzione del pacchetto sono necessari due passaggi.  
  
1.  Quando si seleziona il comando **Converti nel modello di distribuzione del pacchetto** dal menu **Progetto** viene verificata la compatibilità del progetto e di ogni relativo pacchetto con questo modello. I risultati vengono visualizzati nella tabella **Risultati** .  
  
     Se la verifica di compatibilità del progetto o di un pacchetto non viene completata correttamente, per ottenere ulteriori informazioni fare clic su **Non riuscito** nella colonna **Risultato** . Fare clic su **Salva report** per salvare una copia di queste informazioni in un file di testo.  
  
2.  Se il progetto e tutti i pacchetti superano la verifica di compatibilità, fare clic su **OK** per convertire il pacchetto.  
  
> [!NOTE]  
>  Per convertire un progetto nel modello di distribuzione del progetto usare la **Conversione guidata progetto di Integration Services**. Per altre informazioni, vedere [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di progetti e pacchetti](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Distribuzione del pacchetto &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Conversione guidata progetto di Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
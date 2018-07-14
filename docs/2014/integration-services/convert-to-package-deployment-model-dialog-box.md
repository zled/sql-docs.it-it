---
title: Converti in finestra di dialogo del modello di distribuzione di pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1cb982b23645821f6c24c51b4ce4402336c08ea5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233862"
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
  
  

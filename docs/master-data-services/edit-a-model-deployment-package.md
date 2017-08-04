---
title: Modificare un pacchetto di distribuzione di modelli | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bcf1d714605d3f1df2e713e3e8d0311ca1440210
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="edit-a-model-deployment-package"></a>Modificare un pacchetto di distribuzione di modelli
  Questo argomento descrive come distribuire parti selezionate di un modello in MDS, piuttosto che un modello intero. A tale scopo, modificare un pacchetto del modello MDS utilizzando l'Editor pacchetti di modelli.  
  
 La procedura guidata dell'Editor pacchetti di modelli consente di selezionare le entità specifiche, le gerarchie derivate, le viste delle sottoscrizioni e le regole business in un modello che si desidera includere in un pacchetto MDS e quindi successivamente effettuare la distribuzione. È possibile tralasciare quelle parti del modello che non si desidera distribuire. Quando si seleziona un'entità, anche tutti gli oggetti dipendenti di quell'entità vengono selezionati automaticamente.  
  
 Utilizzare l'Editor pacchetti di modelli per selezionare parti di un modello in un file di pacchetto creato dallo strumento MDSModelDeploy (che crea un file di pacchetto che include oggetti e dati) o la Distribuzione guidata modello (che crea un file che include solo la struttura del modello). Dopo avere modificato il modello nel pacchetto, utilizzare lo strumento MDSModelDeploy per distribuire oggetti e dati o la Distribuzione guidata modello per distribuire solo la struttura del modello.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che esista un pacchetto del modello da modificare. Per altre informazioni, vedere [Distribuzione di modelli &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md) e [Creare un pacchetto di distribuzione di modelli tramite la procedura guidata](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) o [Creare un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
### <a name="to-edit-a-model-deployment-package"></a>Per modificare un pacchetto di distribuzione di modelli  
  
1.  In Esplora risorse sul server MDS, passare a *unità*:\Programmi\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Eseguire ModelPackageEditor.exe.  
  
3.  Nella procedura guidata dell'Editor pacchetti di modelli, fare clic su **Sfoglia**, spostarsi nella cartella che contiene i pacchetti, selezionare un pacchetto, quindi fare clic su **Apri**. Scegliere **Avanti**.  
  
4.  Selezionare quelle entità, gerarchie derivate, viste delle sottoscrizioni o regole business che si desidera distribuire. Deselezionare quelli che non si desidera distribuire. Scegliere **Avanti**.  
  
5.  Verificare l'elenco delle selezioni da distribuire. Per apportare modifiche, fare clic su **Indietro** e ripetizione il passaggio 4.  
  
6.  Fare clic su **Sfoglia**, spostarsi nella cartella nella quale si vuole salvare il pacchetto parziale, quindi immettere il nome file del pacchetto parziale (con estensione pkg). Fare clic su **Salva**.  
  
7.  Fare clic su **Fine**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Distribuire un pacchetto di distribuzione di modelli tramite la procedura guidata](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  

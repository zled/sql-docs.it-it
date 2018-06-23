---
title: Distribuzione guidata di Integration Services | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 60bc9f05f7a00075efbda2972cf78d9d169c55d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055737"
---
# <a name="integration-services-deployment-wizard"></a>Distribuzione guidata Integration Services
  Con la Distribuzione guidata [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è possibile distribuire progetti nel catalogo SSISDB in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzando il modello di distribuzione del progetto.  
  
 Per avviare il [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] distribuzione guidata da un progetto aperto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], selezionare **Distribuisci** dal **progetto** menu. Per avviare la procedura guidata in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], espandere il **cataloghi di Integration Services** > **SSISDB** destro del mouse sul nodo in Esplora oggetti, il **progetti** cartella e quindi fare clic su **Distribuisci progetto**.  
  
 La procedura guidata prevede inoltre i quattro passaggi seguenti. Fare clic su **successivo** per passare al passaggio successivo, o **Previous** per tornare al passaggio precedente.  
  
1.  **Seleziona origine** : selezionare il [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] progetto che si desidera distribuire.  
  
2.  **Selezionare la destinazione** – selezionare la destinazione del progetto.  
  
3.  **Revisione** – consente di visualizzare gli elementi selezionati.  
  
4.  **Distribuisci/risultati** : distribuisce il progetto e visualizza i risultati.  
  
## <a name="select-source"></a>Seleziona origine  
 Per distribuire un file di progetto di distribuzione che è stato creato, selezionare **file distribuzione progetto** e immettere il percorso del file con estensione ispac o fare clic su **Sfoglia** per individuarlo nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cartella del progetto. Per distribuire un progetto che si trova nel catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , selezionare **Catalogo di Integration Services**, quindi immettere il nome del server e il percorso del progetto nel catalogo.  
  
 Se si inizia la procedura guidata in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], per impostazione predefinita tramite la procedura guidata viene selezionato il progetto aperto come origine e questo passaggio viene ignorato. Per tornare a questo passaggio e selezionare un'origine diversa, fare clic su **Previous** oppure fare clic su **selezionare l'origine** nel riquadro sinistro.  
  
## <a name="select-destination"></a>Seleziona destinazione  
 Per selezionare la cartella di destinazione per il progetto nel catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , immettere l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o fare clic su **Sfoglia** per effettuare una selezione da un elenco di server. Immettere il percorso del progetto in SSISDB o fare clic su **Sfoglia** per selezionarlo.  
  
 Se si inizia la procedura guidata in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], per impostazione predefinita tramite la procedura guidata viene selezionata l'istanza del server connessa e viene immesso il percorso al progetto selezionato. È possibile modificare questi valori per distribuire il progetto in un percorso diverso.  
  
## <a name="review"></a>Verifica  
 Con la procedura guidata è possibile verificare le impostazioni selezionate prima di distribuire il progetto. È possibile modificare le selezioni facendo clic su **Indietro**o selezionando un qualsiasi passaggio nel riquadro sinistro.  
  
## <a name="deployresults"></a>Distribuisci/Risultati  
 Quando fa clic su **Distribuisci** dal **revisione** pagina, il progetto viene distribuito e il **risultati** pagina consente di visualizzare l'esito positivo o negativo di ciascuna azione. Se l'azione non viene completata correttamente, fare clic su **Non riuscito** nella colonna **Risultato** per visualizzare una spiegazione dell'errore. Fare clic su **salvare Report...**  per salvare i risultati in un file XML.  
  
 Per uscire dalla procedura guidata, fare clic su **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire progetti nel Server Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Distribuzione di progetti e pacchetti](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
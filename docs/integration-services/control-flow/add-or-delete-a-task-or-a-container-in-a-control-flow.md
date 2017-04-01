---
title: "Aggiunta o eliminazione di un&#39;attivit&#224; o un contenitore in un flusso di controllo | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contenitori [Integration Services], aggiunta"
  - "aggiunta di attività"
  - "aggiunta di contenitori"
  - "attività [Integration Services], aggiunta"
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Aggiunta o eliminazione di un&#39;attivit&#224; o un contenitore in un flusso di controllo
  Quando si usa la progettazione dei flussi di controllo, nella casella degli strumenti di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] sono elencate le attività disponibili in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per la compilazione del flusso di controllo in un pacchetto. Per altre informazioni sulla casella degli strumenti, vedere [Casella degli strumenti SSIS](../../integration-services/ssis-toolbox.md).  
  
 Un pacchetto può includere più istanze della stessa attività. Ogni istanza di un'attività è univocamente identificata nel pacchetto e può avere una propria configurazione.  
  
 Se si elimina un'attività, verranno eliminati anche i vincoli di precedenza che la connettono ad altre attività e contenitori nel flusso di controllo.  
  
 Nelle procedure seguenti viene descritto come aggiungere o eliminare un'attività o un contenitore nel flusso di controllo di un pacchetto.  
  
### Per aggiungere un'attività o un contenitore a un flusso di controllo  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** .  
  
4.  Per aprire la **casella degli strumenti**, scegliere **Casella degli strumenti** dal menu **Visualizza**.  
  
5.  Espandere **Elementi flusso di controllo** e **Attività di manutenzione**.  
  
6.  Trascinare attività e contenitori dalla **casella degli strumenti** all'area di progettazione della scheda **Flusso di controllo**.  
  
7.  Connettere un'attività o un contenitore nel flusso di controllo del pacchetto trascinandone il connettore fino a un altro componente nel flusso di controllo.  
  
8.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### Per eliminare un'attività o un contenitore da un flusso di controllo  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo. Eseguire una delle operazioni seguenti:  
  
    -   Fare clic sulla scheda **Flusso di controllo**, fare clic con il pulsante destro del mouse sull'attività o il contenitore da rimuovere e quindi scegliere **Elimina**.  
  
    -   Aprire **Esplora pacchetti**. Nella cartella **File eseguibili** fare clic con il pulsante destro del mouse sull'attività o il contenitore da rimuovere e quindi scegliere **Elimina**.  
  
3.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Contenitori in Integration Services](../../integration-services/control-flow/integration-services-containers.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  
---
title: "Connessione di componenti in un flusso di dati | Microsoft Docs"
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
  - "componenti [Integration Services], connessioni"
  - "connessioni [Integration Services], componenti flusso di dati"
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Connessione di componenti in un flusso di dati
  Questa procedura descrive la connessione dell'output dei componenti di un flusso di dati ad altri componenti dello stesso flusso di dati.  
  
### Per connettere componenti in un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo**, quindi fare doppio clic sull'attività Flusso di dati che contiene il flusso di dati in cui si desidera connettere i componenti.  
  
4.  Nell'area di progettazione della scheda **Flusso di dati** selezionare la trasformazione o l'origine da connettere.  
  
5.  Trascinare la freccia verde dell'output di un'origine o trasformazione a una destinazione o trasformazione. In alcuni componenti flussi di dati sono inclusi output degli errori che è possibile connettere allo stesso modo.  
  
    > [!NOTE]  
    >  Alcuni componenti flussi di dati possono includere più output ed è possibile connettere ogni output a una trasformazione o destinazione diversa.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## Vedere anche  
 [Aggiunta o eliminazione di un componente in un flusso di dati](../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)   
 [Configurazione di un output degli errori in un componente del flusso di dati](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)   
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  
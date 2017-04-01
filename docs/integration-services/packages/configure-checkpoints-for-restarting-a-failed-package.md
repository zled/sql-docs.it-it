---
title: "Configurazione dei checkpoint per il riavvio di un pacchetto non riuscito | Microsoft Docs"
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
  - "checkpoint [Integration Services]"
  - "riavvio dei pacchetti"
  - "avvio dei pacchetti"
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Configurazione dei checkpoint per il riavvio di un pacchetto non riuscito
  Impostando le proprietà relative ai checkpoint, è possibile configurare i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in modo che vengano riavviati dal momento dell'errore, anziché essere eseguiti nuovamente dall'inizio.  
  
### Per configurare un pacchetto per il riavvio  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente il pacchetto che si desidera configurare.  
  
2.  In **Esplora soluzioni** fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** .  
  
4.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dello sfondo dell'area di progettazione del flusso di controllo, quindi scegliere **Proprietà**.  
  
5.  Impostare la proprietà SaveCheckpoints su **True**.  
  
6.  Digitare il nome del file del checkpoint nella proprietà CheckpointFileName.  
  
7.  Impostare la proprietà CheckpointUsage su uno dei due valori seguenti:  
  
    -   Selezionare **Always** per riavviare sempre il pacchetto dal checkpoint.  
  
        > [!IMPORTANT]  
        >  Se il file del checkpoint non è disponibile, viene generato un errore.  
  
    -   Selezionare **IfExists** per riavviare il pacchetto solo se il file del checkpoint è disponibile.  
  
8.  Configurare le attività e i contenitori da cui è possibile riavviare il pacchetto.  
  
    -   Fare clic con il pulsante destro del mouse su un'attività o un contenitore, quindi scegliere **Proprietà**.  
  
    -   Impostare la proprietà FailPackageOnFailure su **True** per ogni attività e contenitore selezionati.  
  
## Vedere anche  
 [Riavvio dei pacchetti tramite checkpoint](../../integration-services/packages/restart-packages-by-using-checkpoints.md)  
  
  
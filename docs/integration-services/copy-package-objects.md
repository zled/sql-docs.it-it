---
title: "Copia di oggetti di pacchetto | Microsoft Docs"
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
  - "flusso di controllo [Integration Services], copia di oggetti"
  - "copia di oggetti di pacchetti [Integration Services]"
  - "flusso di dati [Integration Services], copia di oggetti"
  - "gestioni connessioni [Integration Services], copia"
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Copia di oggetti di pacchetto
  In questo argomento viene descritta la procedura per copiare elementi di un flusso di controllo, elementi di un flusso di dati e gestioni connessioni all'interno di un pacchetto o tra pacchetti diversi.  
  
### Per copiare elementi di un flusso di controllo o di un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente i pacchetti da usare.  
  
2.  In Esplora soluzioni fare doppio clic sui pacchetti tra cui si desidera copiare gli elementi.  
  
3.  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] fare clic sulla scheda corrispondente al pacchetto che contiene gli elementi da copiare e quindi fare clic sulla scheda **Flusso di controllo**, **Flusso di dati** o **Gestori eventi**.  
  
4.  Selezionare gli elementi del flusso di controllo o di dati che si desidera copiare. È possibile selezionare un elemento alla volta, facendo clic sugli elementi desiderati mentre si tiene premuto il tasto MAIUSC, oppure selezionarli come gruppo, trascinando il puntatore del mouse sugli elementi desiderati.  
  
    > [!IMPORTANT]  
    >  Quando si selezionano due elementi connessi, i vincoli di precedenza e i percorsi che li connettono non vengono selezionati automaticamente. Per copiare un flusso di lavoro ordinato, ovvero un segmento di un flusso di controllo o di dati, è necessario copiare anche i vincoli di precedenza e i percorsi.  
  
5.  Fare clic con il pulsante destro del mouse su un elemento selezionato e quindi scegliere **Copia**.  
  
6.  Se si copiano elementi in un pacchetto diverso, fare clic sul pacchetto in cui si desidera copiare gli elementi e quindi fare clic sulla scheda corrispondente al tipo di elemento.  
  
    > [!IMPORTANT]  
    >  È possibile copiare un flusso di dati in un pacchetto solo se il pacchetto contiene almeno un'attività Flusso di dati.  
  
7.  Fare clic con il pulsante destro del mouse e scegliere **Incolla**.  
  
### Per copiare gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto da usare.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto.  
  
3.  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] fare clic sulla scheda **Flusso di controllo**, **Flusso di dati** o **Gestori eventi**.  
  
4.  Nella sezione **Gestioni connessioni** fare clic con il pulsante destro del mouse sulla gestione connessione e quindi scegliere **Copia**. È possibile copiare una sola gestione connessione alla volta.  
  
5.  Se si copiano elementi in un pacchetto diverso, fare clic sul pacchetto in cui si vogliono copiare gli elementi e quindi fare clic sulla scheda **Flusso di controllo**, **Flusso di dati** o **Gestori eventi**.  
  
6.  Fare clic con il pulsante destro del mouse nella sezione **Gestioni connessioni** e scegliere **Incolla**.  
  
## Vedere anche  
 [Flusso di controllo](../integration-services/control-flow/control-flow.md)   
 [Flusso di dati](../integration-services/data-flow/data-flow.md)   
 [Connessioni in Integration Services &#40;SSIS&#41;](../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Copia di elementi di progetto](../Topic/Copy%20Project%20Items.md)  
  
  
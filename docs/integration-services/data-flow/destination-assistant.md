---
title: Assistente destinazione | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.destinationassistant.f1
- sql13.DTS.DESIGNER.DESTINATIONASSIST.F1
ms.assetid: 10a40921-a2c2-4ac8-be28-311f8500fbf6
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: aebe1dfa1046bddfa86e48aecdd68930caf3285c
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="destination-assistant"></a>Assistente destinazione
  Il componente Assistente destinazione consente di creare un componente di destinazione e una gestione connessione. Il componente si trova nella sezione **Preferiti** della casella degli strumenti di SSIS.  
  
> [!NOTE]  
>  Assistente destinazione sostituisce il progetto Connessioni in Integration Services e la procedura guidata corrispondente.  

## <a name="add-a-destination-with-destination-assistant"></a>Aggiungere una destinazione con Assistente destinazione
Questo argomento illustra i passaggi necessari per aggiungere una nuova destinazione usando Assistente destinazione ed elenca inoltre le opzioni disponibili nella finestra di dialogo **Aggiungi nuova destinazione** che viene visualizzata quando si trascina Assistente destinazione in Progettazione SSIS.  

1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a cui si desidera aggiungere un componente di destinazione.  
  
2.  Trascinare il componente **Assistente destinazione** dalla casella degli strumenti di SSIS alla scheda **Flusso di dati** . Verrà visualizzata la finestra di dialogo **Aggiungi nuova destinazione** . Nella sezione successiva vengono forniti i dettagli relativi alle opzioni disponibili nella finestra di dialogo.  
  
3.  Selezionare il tipo della destinazione nell'elenco **Tipi**.  
  
4.  Selezionare una gestione connessione esistente nel **gestioni connessioni** elenco oppure selezionare  **\<nuovo >** per creare una nuova gestione connessione.  
  
5.  Se si seleziona una gestione connessione esistente, fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi nuova destinazione**. La destinazione e le gestioni connessioni verranno aggiunte al flusso di dati.  
  
6.  Se si fa clic  **\<nuovo >** per creare una nuova gestione connessione, verrà visualizzato un **Connection Manager** nella finestra di dialogo che consente di specificare i parametri per la connessione. Dopo avere completato la creazione della nuova gestione connessione, la destinazione e la gestione connessione saranno visibili in Progettazione SSIS. 
  
## <a name="add-new-destination-dialog-box"></a>Aggiungere la finestra di dialogo Nuova destinazione
La tabella seguente elenca le opzioni disponibili per il **Aggiungi nuova destinazione** la finestra di dialogo.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tipi|Selezionare il tipo di destinazione a cui si desidera connettersi.|  
|Gestioni connessioni|Selezionare una gestione connessione esistente oppure fare clic su  **\<nuovo >** per creare una nuova gestione connessione.|  
|Mostra solo installati|Consente di specificare se visualizzare solo le destinazioni installate.|  
|OK|Fare clic per salvare le modifiche e aprire eventuali finestre di dialogo successive per configurare opzioni aggiuntive.|  


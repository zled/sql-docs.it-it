---
title: Assistente origine | Documenti Microsoft
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
- sql13.dts.designer.sourceassistant.f1
- sql13.dts.designer.addNewSource.f1
ms.assetid: 5ca9d821-7d61-4727-9133-5f9cb485c7f3
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9b7406edf9f7234db739730473772d77c42399ec
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="source-assistant"></a>Assistente origine
  Il componente Assistente origine consente di creare un componente di origine e una gestione connessione. Il componente si trova nella sezione **Preferiti** della casella degli strumenti di SSIS.  
  
> [!NOTE]  
>  Assistente origine sostituisce il progetto Connessioni in Integration Services e la procedura guidata corrispondente.  
  
## <a name="add-a-source-with-source-assistant"></a>Aggiungere un'origine con Assistente origine
In questa sezione viene descritta la procedura per aggiungere una nuova origine utilizzando Assistente origine e sono elencate le opzioni disponibili nel **Aggiungi nuova origine** finestra di dialogo che verrà visualizzato quando si trascina Assistente origine in Progettazione SSIS.  

1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a cui si vuole aggiungere un componente di origine.  
  
2.  Trascinare il componente **Assistente origine** dalla casella degli strumenti di SSIS alla scheda **Flusso di dati** . Verrà visualizzata la finestra di dialogo **Aggiungi nuova origine** . Nella sezione successiva vengono forniti i dettagli relativi alle opzioni disponibili nella finestra di dialogo.  
  
3.  Selezionare il tipo della destinazione nell'elenco **Tipi**.  
  
4.  Selezionare una gestione connessione esistente nel **gestioni connessioni** elenco oppure selezionare  **\<nuovo >** per creare una nuova gestione connessione.  
  
5.  Se si seleziona una gestione connessione esistente, fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi nuova destinazione**. La destinazione e le gestioni connessioni verranno aggiunte al flusso di dati.  
  
6.  Se si fa clic  **\<nuovo >** per creare una nuova gestione connessione, verrà visualizzato un **Connection Manager** nella finestra di dialogo che consente di specificare i parametri per la connessione. Dopo avere completato la creazione della nuova gestione connessione, la destinazione e la gestione connessione saranno visibili in Progettazione SSIS.  

## <a name="add-new-source-dialog-box"></a>Aggiungere la finestra di dialogo Nuova origine
La tabella seguente elenca le opzioni disponibili nel **Aggiungi nuova origine** la finestra di dialogo.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tipi|Selezionare il tipo di origine a cui si desidera connettersi.|  
|Gestioni connessioni|Selezionare una gestione connessione esistente oppure fare clic su  **\<nuovo >** per creare una nuova gestione connessione.|  
|Mostra solo installati|Consente di specificare se visualizzare solo le origini installate.|  
|OK|Fare clic per salvare le modifiche e aprire eventuali finestre di dialogo successive per configurare opzioni aggiuntive.| 
  

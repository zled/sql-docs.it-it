---
title: Aggiungere un'origine tramite Assistente origine | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e850b7c-4b89-42ad-b0a6-d63ac7cc9568
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7ef237b263aa37d3998b8634b18926850d2cb4f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171070"
---
# <a name="add-a-source-using-source-assistant"></a>Aggiunta di un'origine tramite Assistente origine
  Questo argomento illustra i passaggi necessari per aggiungere una nuova origine usando Assistente origine ed elenca le opzioni disponibili nella finestra di dialogo **Aggiungi nuova origine** che viene visualizzata quando si trascina Assistente origine in Progettazione SSIS.  
  
### <a name="to-use-source-assistant-to-add-a-source"></a>Per utilizzare Assistente origine per aggiungere un'origine  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] a cui si vuole aggiungere un componente di origine.  
  
2.  Trascinare il componente **Assistente origine** dalla casella degli strumenti di SSIS alla scheda **Flusso di dati** . Verrà visualizzata la finestra di dialogo **Aggiungi nuova origine** . Nella sezione successiva vengono forniti i dettagli relativi alle opzioni disponibili nella finestra di dialogo.  
  
3.  Selezionare il tipo della destinazione nell'elenco **Tipi**.  
  
4.  Selezionare una gestione connessione esistente nell'elenco **Gestioni connessioni** oppure selezionare **\<Nuova>** per creare una nuova gestione connessione.  
  
5.  Se si seleziona una gestione connessione esistente, fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi nuova destinazione**. La destinazione e le gestioni connessioni verranno aggiunte al flusso di dati.  
  
6.  Se si fa clic su **\<Nuova>** per creare una nuova gestione connessione, viene visualizzata la finestra di dialogo **Gestione connessione** in cui è possibile specificare i parametri per la connessione. Dopo avere completato la creazione della nuova gestione connessione, la destinazione e la gestione connessione saranno visibili in Progettazione SSIS.  
  
  
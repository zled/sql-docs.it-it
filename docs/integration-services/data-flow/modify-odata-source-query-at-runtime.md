---
title: Fornire una Query di origine OData in fase di esecuzione | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 9da1f1be0a790d01f9403d6fc05a5c1498c0ee8b
ms.contentlocale: it-it
ms.lasthandoff: 08/23/2017

---
# <a name="provide-an-odata-source-query-at-runtime"></a>Fornire una Query di origine OData in fase di esecuzione
 È possibile modificare la query di origine OData in fase di esecuzione tramite l'aggiunta di un *espressione* per il **[origine OData]. [ Query]** proprietà dell'attività flusso di dati.  
  
 Le colonne restituite devono essere le stesse colonne che sono state restituite in fase di progettazione. in caso contrario, un errore si verifica quando viene eseguito il pacchetto. Assicurarsi di specificare le stesse colonne (nello stesso ordine) quando si utilizza l'opzione query $select. Un'alternativa più sicura all'utilizzo dell'opzione $select consiste nel deselezionare le colonne non desiderate direttamente dall'interfaccia utente del componente di origine.  
  
 Sono disponibili alcune modalità differenti per impostare dinamicamente il valore di query in fase di esecuzione. Ecco alcuni dei metodi più comuni.  
  
## <a name="provide-the-query-as-a-parameter"></a>Specificare la query come parametro  
 La procedura seguente viene illustrato come esporre la query utilizzata da un componente origine OData come parametro del pacchetto.  
  
1.  Fare clic con il pulsante destro del mouse sull' **attività Flusso di dati** e scegliere l’opzione **Imposta parametri**. opzione.  
  
2.  Nel **imposta parametri** finestra di dialogo Seleziona **[\<nome del componente di origine OData >]. [ Query]** per **proprietà**.  
  
3.  Scegliere se **creare un nuovo parametro** o **usare un parametro esistente**.  
  
4.  Se si seleziona **creare un nuovo parametro**:  
  
    1.  Immettere un **nome** e una **descrizione** per il parametro.  
  
    2.  Specificare il **valore** predefinito per il parametro.  
  
    3.  Specificare l' **ambito** (**pacchetto** o **progetto**) per il parametro.  
  
    4.  Specificare se il parametro è **obbligatorio** o meno.  
  
5.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
## <a name="provide-the-query-with-an-expression"></a>Specifica un'espressione di query
 Questo metodo è utile quando si desidera creare dinamicamente la stringa di query in fase di esecuzione.
  
1.  Selezionare il **attività flusso di dati** che contiene il **origine OData**.  
  
2.  Nella finestra **Proprietà** selezionare la proprietà **Espressioni** .  
  
3.  Fare clic sul pulsante con i puntini di sospensione (...) pulsante (puntini di sospensione) per visualizzare il **Editor espressioni di proprietà**.  
  
4.  Selezionare la proprietà **[Origine OData].[Query]** .  
  
5.  Fare clic sul pulsante con i puntini di sospensione (...) () con i puntini **espressione**.  
  
6.  Immettere l' **espressione**.  
  
7.  Scegliere **OK**.  
  
> [!NOTE]  
> Quando si utilizza questo approccio, è necessario assicurarsi che i valori impostati siano URL correttamente codificati. Alla ricezione di valori dall'input utente, ad esempio l'impostazione di singoli valori di opzioni query da un parametro, è necessario assicurarsi che i valori siano convalidati per evitare potenziali attacchi SQL injection.  
  
  


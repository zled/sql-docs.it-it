---
title: "Modificare la query di origine OData in fase di esecuzione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Modificare la query di origine OData in fase di esecuzione
  È possibile modificare la query di origine OData in fase di esecuzione aggiungendo un'espressione alla proprietà **[Origine OData].[Query]** dell'attività Flusso di dati.  
  
 Si noti che le colonne devono essere le stesse di quelle utilizzate in fase di progettazione; in caso contrario, verrà visualizzato un errore al momento dell'esecuzione del pacchetto. Assicurarsi di specificare le stesse colonne (nello stesso ordine) quando si utilizza l'opzione query $select. Un'alternativa più sicura all'utilizzo dell'opzione $select consiste nel deselezionare le colonne non desiderate direttamente dall'interfaccia utente del componente di origine.  
  
 Sono disponibili alcune modalità differenti per impostare dinamicamente il valore di query in fase di esecuzione. Di seguito sono riportati alcuni dei metodi più comuni.  
  
## Esposizione della query come parametro  
 Nella procedura seguente sono riportati i passaggi per esporre la query utilizzata da un componente di origine OData come parametro nel pacchetto.  
  
1.  Fare clic con il pulsante destro del mouse sull'**attività Flusso di dati** e scegliere l’opzione **Imposta parametri**. opzione.  
  
2.  Nella finestra di dialogo **Imposta parametri** selezionare **[\< nome del componente di origine OData>].[Query]** per **Proprietà**.  
  
3.  Scegliere se **creare un nuovo parametro** o **usare un parametro esistente**.  
  
4.  Se si seleziona **Crea nuovo parametro**, eseguire le operazioni seguenti:  
  
    1.  Immettere un **nome** e una **descrizione** per il parametro.  
  
    2.  Specificare il **valore** predefinito per il parametro.  
  
    3.  Specificare l'**ambito** (**pacchetto** o **progetto**) per il parametro.  
  
    4.  Specificare se il parametro è **obbligatorio** o meno.  
  
5.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
## Utilizzo di un'espressione  
 Questo metodo è utile quando si desidera creare dinamicamente la stringa di query in fase di esecuzione. In questo esempio, la variabile MaxRows verrà impostata in altro modo (script, parametro e così via).  
  
1.  Selezionare l'**attività Flusso di dati** contenente l'**Origine OData**.  
  
2.  Nella finestra **Proprietà** selezionare la proprietà **Espressioni**.  
  
3.  Fare clic sul pulsante con i puntini di sospensione (...) per visualizzare **Editor espressioni di proprietà**.  
  
4.  Selezionare la proprietà **[Origine OData].[Query]**.  
  
5.  Fare clic sul pulsante con i puntini di sospensione (...) per **Espressione**.  
  
6.  Immettere l'**espressione**.  
  
7.  Scegliere **OK**.  
  
> [!WARNING]  
>  Si noti che quando si utilizza questo approccio, è necessario assicurarsi che i valori impostati siano URL correttamente codificati. Alla ricezione di valori dall'input utente, ad esempio l'impostazione di singoli valori di opzioni query da un parametro, è necessario assicurarsi che i valori siano convalidati per evitare potenziali attacchi SQL injection.  
  
  
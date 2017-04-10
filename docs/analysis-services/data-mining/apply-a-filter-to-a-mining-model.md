---
title: "Applicare un filtro a un modello di data mining | Microsoft Docs"
ms.custom: ""
ms.date: "03/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtro dei modelli [data mining]"
  - "filtri [data mining]"
  - "filtraggio delle righe di input [Analysis Services]"
  - "applicazione di filtri ai dati [Analysis Services]"
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 17
---
# Applicare un filtro a un modello di data mining
  Se la struttura di data mining contiene una tabella nidificata, è possibile applicare un filtro alla tabella del case, alla tabella nidificata o a entrambe.  
  
 Nella procedura seguente viene illustrato come creare entrambi i tipi di filtro: filtri di case e filtri sulle righe della tabella nidificata.  
  
 La condizione sulla tabella del case restringe i clienti a quelli con il reddito compreso tra 30000 e 40000. La condizione sulla tabella nidificata restringe i clienti a quelli che non hanno acquistato un determinato articolo.  
  
 La condizione di filtro completa creata in questo esempio è la seguente:  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### Per creare un filtro di case su un modello di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining da filtrare.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     -oppure-  
  
     Selezionare il modello. quindi scegliere **Imposta filtro modello** dal menu **Modello di data mining**.  
  
4.  Nella finestra di dialogo **Filtro modello** fare clic sulla riga superiore nella griglia della casella di testo **Colonna struttura di data mining** .  
  
5.  Se l'origine dati contiene una singola tabella flat, l'elenco a discesa visualizza solo i nomi delle colonne di tale tabella.  
  
     Se la struttura di data mining contiene più tabelle, l'elenco mostra i nomi delle tabelle di origine. I nomi delle colonne vengono visualizzati solo dopo la selezione di una tabella.  
  
     Se la struttura di data mining contiene una tabella del case e una tabella nidificata, l'elenco a discesa mostra le colonne dalla tabella del case e il nome della tabella nidificata.  
  
6.  Selezionare una colonna dall'elenco a discesa.  
  
     L'icona a sinistra della casella di testo cambierà per indicare che l'elemento selezionato è una tabella o una colonna.  
  
7.  Fare clic sulla casella di testo **Operatore** e selezionare un operatore dall'elenco. Gli operatori validi variano a seconda del tipo di dati della colonna selezionata.  
  
8.  Fare clic nella casella di testo **Valore** e digitare un valore.  
  
     Ad esempio, selezioni **Income** come colonna, selezionare l'operatore maggiore di (>) e quindi digitare **30000**.  
  
9. Fare clic sulla riga successiva nella griglia.  
  
     La condizione di filtro creata viene aggiunta automaticamente nella casella di testo Espressione. Ad esempio, `[Income] > '30000'`  
  
10. Fare clic nella casella di testo **AND/OR** nella riga successiva della griglia per aggiungere una condizione.  
  
     Ad esempio, per creare una condizione BETWEEN, selezionare **AND** nell'elenco a discesa di operandi logici.  
  
11. Selezionare un operatore e digitare un valore come descritto nei passaggi 7 e 8.  
  
     Ad esempio, selezionare nuovamente **Income** come colonna, selezionare l'operatore minore di (<) e quindi digitare **40000**.  
  
12. Fare clic sulla riga successiva nella griglia.  
  
13. La condizione di filtro nella casella di testo Espressione viene aggiornata automaticamente per includere la nuova condizione. L'espressione completa è la seguente: `[Income] > '30000'AND [Income] < '40000'`  
  
### Per aggiungere un filtro nella tabella nidificata in un modello di data mining  
  
1.  Nella finestra di dialogo **Filtro modello \<nome>** fare clic in una riga vuota della griglia sotto **Colonna struttura di data mining**.  
  
2.  Selezionare il nome della tabella nidificata dall'elenco a discesa.  
  
     L'icona a sinistra della casella di testo cambia per indicare che l'elemento selezionato è il nome di una tabella.  
  
3.  Fare clic nella casella di testo **Operatore** e selezionare **Contiene** o **Non contiene**.  
  
     Queste sono le uniche condizioni disponibili per la tabella nidificata nella finestra di dialogo **Filtro modello** , perché la tabella del case è stata limitata solo ai case che contengono un determinato valore nella tabella nidificata. Il valore per la condizione nella tabella nidificata verrà impostato nel passaggio successivo.  
  
4.  Fare clic sulla casella **Valore** e quindi sul pulsante (**…**) per creare un'espressione.  
  
     Verrà visualizzata la finestra di dialogo **Filtro \<nome>**. Questa finestra di dialogo consente di impostare condizioni solo nella tabella corrente, che in questo caso è la tabella nidificata.  
  
5.  Fare clic sulla casella **Colonna struttura di data mining** e selezionare un nome di colonna dagli elenchi a discesa di colonne della tabella nidificata.  
  
6.  Fare clic su **Operatore** e selezionare un operatore dall'elenco di operatori validi per la colonna.  
  
7.  Fare clic su **Valore** e digitare un valore.  
  
     Ad esempio, per **Colonna struttura di data mining** selezionare **Model**. Per **Operatore**, selezionare **<>** e digitare il valore **Water Bottle**. Questa condizione crea l'espressione di filtro seguente:  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  Poiché il numero di attributi della tabella nidificata è potenzialmente illimitato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non viene fornito un elenco di valori possibili da cui effettuare una selezione. È necessario digitare il valore esatto. Inoltre, non è possibile utilizzare un operatore LIKE in una tabella nidificata.  
  
1.  Se necessario, aggiungere altre condizioni. Per combinare le condizioni, selezionare **AND** o **OR** nella casella **AND/OR** a sinistra della griglia **Condizioni**. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  Nella finestra di dialogo **Filtro modello** esaminare le condizioni create utilizzando la finestra di dialogo **Filtro** . Le condizioni per la tabella nidificata vengono aggiunte alle condizioni per la tabella del case e il set completo di condizioni di filtro viene visualizzato nella casella di testo **Espressione** .  
  
3.  È possibile fare clic su **Modifica query** per modificare manualmente l'espressione di filtro (facoltativo).  
  
    > [!NOTE]  
    >  Se si modifica manualmente una parte di un'espressione di filtro, la griglia verrà disabilitata e da quel momento sarà necessario utilizzare l'espressione di filtro solo in modalità di modifica di testo. Per ripristinare la modalità di modifica della griglia, è necessario cancellare l'espressione di filtro e ricominciare.  
  
4.  
  
## Vedere anche  
 [Filtri per i modelli di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Eliminare un filtro da un modello di data mining](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
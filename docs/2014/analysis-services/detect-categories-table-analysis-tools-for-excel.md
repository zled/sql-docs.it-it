---
title: Rileva categorie (strumenti di analisi tabelle per Excel) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d46840e2c2f7de1d56d6b528706ae908e7627a3e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065950"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>Rileva categorie (Strumenti di analisi tabelle per Excel)
  ![Pulsante di rileva categorie sulla barra multifunzione](media/tat-detectcat.gif "pulsante rileva categorie sulla barra multifunzione")  
  
 Il **rileva categorie** strumento rileva automaticamente le righe in una tabella con caratteristiche simili.  
  
 Al termine dell'esecuzione dello strumento, viene creato un report in cui sono elencate tutte le categorie trovate, insieme alle relative caratteristiche distintive. Per impostazione predefinita, nella tabella dati contenente la categoria proposta viene aggiunta una nuova colonna per ogni riga di dati. È quindi possibile esaminare le categorie e rinominarle.  
  
## <a name="using-the-detect-categories-tool"></a>Utilizzo dello strumento Rileva categorie  
  
1.  Aprire una tabella di Excel.  
  
2.  Fare clic su **rileva categorie**.  
  
3.  Specificare le colonne da utilizzare nell'analisi. È possibile deselezionare le colonne contenenti valori distinti, ad esempio nomi o ID di record, poiché non sono utili per l'analisi.  
  
4.  È possibile specificare il numero massimo di categorie da creare. Per impostazione predefinita, vengono create automaticamente tutte le categorie trovate dallo strumento.  
  
5.  Fare clic su **Esegui**.  
  
6.  Tramite lo strumento viene creato un nuovo foglio di lavoro, denominato Report categorie, contenente l'elenco delle categorie e le relative caratteristiche.  
  
 Per ulteriori informazioni su come specificare le opzioni per lo strumento, vedere [rilevare finestra di dialogo categorie (strumenti di analisi tabelle per Excel)](detect-categories-table-analysis-tools-for-excel.md).  
  
## <a name="understanding-the-categories-report"></a>Informazioni su Report categorie  
 Il **Report categorie** contiene due tabelle **elenco categorie** e **caratteristiche categoria**e un **profili categoria** grafico.  
  
### <a name="category-list"></a>Elenco di categorie  
 Nella prima tabella sono elencate le categorie trovate. Il **conteggio delle righe** colonna indica il numero di righe di dati sono stato assegnato a ogni categoria.  
  
 Il modello crea nomi temporanei per ogni categoria, ma è possibile rinominare le categorie come si desidera. Ad esempio, nell'esempio seguente, la prima categoria rinominata **Low Income**, perché questo è l'attributo principale del cluster.  
  
 ![report creato dallo strumento rileva categorie](media/dm13-tat-detectcat-report1.gif "report creato dallo strumento rileva categorie")  
  
 Non appena si digita la nuova etichetta, la modifica viene propagata a tutti gli altri grafici e all'elenco di categorie aggiunto nel foglio di lavoro dati di origine.  
  
### <a name="category-characteristics"></a>Caratteristiche categoria  
 Nella seconda tabella, **caratteristiche categoria**, Mostra i dettagli relativi alla struttura di ogni categoria. Fare clic sui **filtro** pulsante in cima il **categoria** colonna per visualizzare lo stato attivo su una o poche categorie.  
  
 ![report creato dallo strumento rileva categorie](media/dm13-tat-detectcat-report2.gif "report creato dallo strumento rileva categorie")  
  
 L'ombreggiatura della colonna **importanza relativa**, indica il livello di importanza della combinazione di attributo e il valore è un fattore di distinzione. Più è lunga la barra, più è probabile che l'attributo sia fortemente rappresentativo della categoria.  
  
### <a name="categories-profile-chart"></a>Grafico Profili categoria  
 Il grafico finale il **Report categorie** foglio di lavoro **profili categoria**, è un oggetto interattivo **grafico Pivot** che è possibile utilizzare per riorganizzare e nascondere campi, filtrare i valori e personalizzare l'aspetto del grafico.  
  
 Excel 2013 fornisce ora **gli stili del grafico** e **elementi del grafico** direttamente nell'area di progettazione che semplificano migliorare la progettazione del grafico.  
  
 ![report creato dallo strumento rileva categorie](media/dm13-tat-detectcat-report3.gif "report creato dallo strumento rileva categorie")  
  
## <a name="requirements"></a>Requisiti  
 Il **rileva categorie** strumento è previsti requisiti relativi alla quantità o al tipo di dati.  
  
> [!NOTE]  
>  Quando si usa il **rileva categorie** strumento, viene creata una nuova colonna, categoria, nella tabella dati originale. Se si lascia questa colonna nella tabella dati e quindi si eseguono successivamente operazioni di data mining, è possibile che i risultati vengano falsati dalla presenza di tale colonna. Per evitare questo problema, è consigliabile creare una copia della tabella dati senza la colonna Categoria prima di utilizzare altri strumenti di data mining.  
  
## <a name="related-tools"></a>Strumenti correlati  
 Quando il **rileva categorie** strumento analizza i dati, crea una struttura di data mining e un modello di data mining utilizzando il [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo Clustering.  
  
 Dopo aver creato un modello di data mining utilizzando il **analizza fattori di influenza chiave** strumento, è possibile utilizzare il Client di Data Mining per Excel per esplorare il modello e analizzare le relazioni più dettagliatamente. Il Client di data mining per Excel è un componente aggiuntivo separato in cui sono disponibili funzionalità di data mining più avanzate. Per informazioni, vedere [esplorazione di modelli in Excel &#40;componenti aggiuntivi Data Mining di SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).  
  
 Per ulteriori informazioni sull'utilizzo di modellazione dei dati funzionalità nel Client di Data Mining per Excel, vedere [creazione di un modello di Data Mining](creating-a-data-mining-model.md).  
  
 Per ulteriori informazioni sull'algoritmo utilizzato per il **rileva categorie** strumento, vedere l'argomento "Algoritmo Microsoft Clustering" nella [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] documentazione Online.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di analisi tabelle per Excel](table-analysis-tools-for-excel.md)  
  
  
---
title: "Creazione e gestione dei cataloghi full-text | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cataloghi full-text [SQL Server], creazione"
  - "ricerca full-text [SQL Server], uso di SQL Server Management Studio"
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Creazione e gestione dei cataloghi full-text
  Un catalogo full-text è un oggetto virtuale che non appartiene ad alcun filegroup. Si tratta di un concetto logico che fa riferimento a un gruppo di indici full-text.  
  
##  <a name="creating"></a> Creazione di un catalogo full-text  
  
#### Per creare un catalogo full-text  
  
1.  In Esplora oggetti espandere il server, quindi **Database** e infine il database in cui si vuole creare il catalogo full-text.  
  
2.  Espandere **Archivio**, quindi fare clic con il pulsante destro del mouse su **Cataloghi full-text**.  
  
3.  Selezionare **Nuovo catalogo full-text**.  
  
4.  Nella finestra di dialogo **Nuovo catalogo full-text** specificare le informazioni per il catalogo da creare. Per altre informazioni, vedere [Nuovo catalogo full-text &#40;pagina Generale&#41;](../Topic/New%20Full-Text%20Catalog%20\(General%20Page\).md).  
  
    > [!NOTE]  
    >  Gli ID dei cataloghi full-text iniziano da 00005 e vengono incrementati di un'unità per ogni catalogo creato.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
   
  
##  <a name="props"></a> Visualizzazione delle proprietà di un catalogo full-text  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Per ottenere il valore di varie proprietà di indicizzazione full-text, è possibile usare funzioni quali FULLTEXTCATALOGPROPERTY. Queste informazioni sono utili per l'amministrazione e la risoluzione dei problemi relativi alla ricerca full-text.  
  
 Nella tabella seguente sono elencate le proprietà correlate ai cataloghi full-text.  
  
|Proprietà|Descrizione|Funzione|  
|--------------|-----------------|--------------|  
|**AccentSensitivity**|Impostazione relativa alla distinzione tra caratteri accentati e non accentati.|[FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|  
|**ImportStatus**|Indica se il catalogo full-text viene importato o meno.|FULLTEXTCATALOGPROPERTY|  
|**IndexSize**|Dimensione del catalogo full-text in megabyte (MB).|FULLTEXTCATALOGPROPERTY|  
|**ItemCount**|Numero delle voci indicizzate incluse attualmente nel catalogo full-text.|FULLTEXTCATALOGPROPERTY|  
|**MergeStatus**|Indica se è in corso un'unione nell'indice master.|FULLTEXTCATALOGPROPERTY|  
|**PopulateCompletionAge**|Differenza espressa in secondi tra il completamento dell'ultimo popolamento di indici full-text e la data 01/01/1990 00:00:00.|FULLTEXTCATALOGPROPERTY|  
|**PopulateStatus**|Stato popolamento.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|**UniqueKeyCount**|Numero di chiavi univoche nel catalogo full-text.|FULLTEXTCATALOGPROPERTY|  
  
   
  
##  <a name="rebuildone"></a> Ricompilazione di un catalogo full-text  
  
#### Per ricompilare un catalogo full-text  
  
1.  In Esplora oggetti espandere il server, quindi **Database** e infine il database contenente il catalogo full-text che si vuole ricompilare.  
  
2.  Espandere **Archivio** e quindi **Cataloghi full-text**.  
  
3.  Fare clic con il pulsante destro sul nome del catalogo full-text da ricompilare e scegliere **Ricompila**.  
  
4.  Quando viene visualizzato il messaggio **Eliminare il catalogo full-text e ricompilarlo?**, fare clic su **OK**.  
  
5.  Nella finestra di dialogo **Ricompila catalogo full-text** fare clic su **Chiudi**.  
  
   
  
##  <a name="rebuildall"></a> Ricompilazione di tutti i cataloghi full-text per un database  
  
#### Per ricompilare i cataloghi full-text di un database  
  
1.  In Esplora oggetti espandere il server, quindi **Database** e infine il database contenente i cataloghi full-text da ricompilare.  
  
2.  Espandere **Archivio**, quindi fare clic con il pulsante destro del mouse su **Cataloghi full-text**.  
  
3.  Scegliere **Ricompila tutto**.  
  
4.  Quando viene visualizzato il messaggio **Eliminare tutti i cataloghi full-text e ricompilarli?**, fare clic su **OK**.  
  
5.  Nella finestra di dialogo **Ricompila tutti i cataloghi full-text** scegliere **Chiudi**.  
  
  
  
##  <a name="removing"></a> Rimozione di un catalogo full-text da un database  
  
#### Per rimuovere un catalogo full-text da un database  
  
1.  In Esplora oggetti espandere il server, quindi **Database** e infine il database contenente il catalogo full-text che si vuole rimuovere.  
  
2.  Espandere **Archivio** e quindi **Cataloghi full-text**.  
  
3.  Fare clic con il pulsante destro del mouse sul catalogo full-text da rimuovere e quindi scegliere **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetti** fare clic su **OK**.  
  
  
## Vedere anche  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)  
  
  
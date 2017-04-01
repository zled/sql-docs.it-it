---
title: "Generazione automatica di un set di filtri di join tra gli articoli di merge (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "generazione automatica di filtri join"
  - "filtri di join"
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Generazione automatica di un set di filtri di join tra gli articoli di merge (SQL Server Management Studio)
  Generare automaticamente un set di filtri di join nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Se si genera automaticamente un set di filtri di join nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo dopo l'inizializzazione delle sottoscrizioni della pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni dopo aver apportato la modifica. Per ulteriori informazioni sui requisiti per le modifiche alle proprietà, vedere [Modifica proprietà della pubblicazione e articolo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 È possibile creare manualmente i filtri join per un set di tabelle o generarli automaticamente durante la replica in base alle relazioni definite nelle tabelle tra la chiave esterna e la chiave primaria. Per ulteriori informazioni sulla creazione manuale di filtri join, vedere [definizione e modifica di un Join filtro tra articoli di Merge](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
### Per generare automaticamente un set di filtri join tra articoli di merge  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, fare clic su **Aggiungi**, e quindi fare clic su **Genera filtri automaticamente**.  
  
    > [!NOTE]  
    >  La generazione automatica dei filtri comporta l'eliminazione dei filtri di riga o dei filtri join esistenti nella pubblicazione. È possibile aggiungere filtri dopo averne generato automaticamente un set.  
  
2.  Per creare un filtro di riga seguire la procedura della finestra di dialogo **Genera filtri** . Il filtro di riga viene quindi esteso alle tabelle relative alla tabella filtrata mediante le relazioni tra chiave primaria e chiave esterna.  
  
    1.  Selezionare una tabella da filtrare dall'elenco a discesa.  
  
    2.  Creare un'istruzione di filtro nella casella di testo **Istruzione per il filtro** . È possibile digitare direttamente nell'area di testo nonché trascinare colonne dalla casella di riepilogo **Colonne** .  
  
         L'area di testo **Istruzione per il filtro** contiene il testo predefinito, nel formato seguente:  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         Non è possibile modificare il testo predefinito. Digitare la clausola di filtro per un filtro di riga statico o per un filtro di riga con parametri dopo la parola chiave WHERE utilizzando la sintassi SQL standard. La clausola di filtro completa per un filtro di riga con parametri è simile alla seguente:  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         Per la clausola WHERE è consigliabile usare nomi in due parti. I nomi in tre e quattro parti non sono supportati.  
  
    3.  Specificare le opzioni di filtro.  
  
         Selezionare l'opzione corrispondente alla modalità di condivisione dei dati tra i Sottoscrittori, ovvero **Una riga di questa tabella verrà inviata a più sottoscrizioni** o **Una riga di questa tabella verrà inviata a una sola sottoscrizione**. Selezionando **Una riga di questa tabella verrà inviata a una sola sottoscrizione**è possibile ottimizzare le prestazioni della replica di tipo merge archiviando ed elaborando una minore quantità di metadati. È tuttavia necessario garantire che i dati vengano partizionati in modo da non consentire la replica di una riga in più Sottoscrittori. Per altre informazioni, vedere la sezione relativa all'impostazione delle opzioni delle partizioni nell'argomento [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Il filtro specificato viene analizzato ed eseguito sulla tabella nella clausola SELECT. Se nell'istruzione di filtro sono presenti errori di sintassi o di altro tipo, verrà visualizzato un apposito messaggio di notifica e sarà possibile modificare l'istruzione.  
  
     Al termine dell'analisi dell'istruzione, i filtri join necessari vengono creati e visualizzati dalla replica nel riquadro **Tabelle filtrate** della pagina **Filtro righe tabella** o **Filtra righe** . Se i filtri vengono generati mediante la Creazione guidata nuova pubblicazione e non è stato ancora configurato il server di distribuzione per il server di pubblicazione sul quale viene eseguita questa procedura guidata, verrà richiesto di procedere a tale configurazione.  
  
4.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
### Per modificare un filtro generato automaticamente  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **filtro righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **modificare**.  
  
2.  Nella finestra di dialogo **Modifica filtro** o **Modifica join** modificare il filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Per eliminare un filtro generato automaticamente  
  
1.  Nel **filtro righe tabella** pagina della procedura guidata nuova pubblicazione o **Filtra righe** pagina della **Proprietà pubblicazione - \< pubblicazione>**, selezionare un filtro nel **tabelle filtrate** riquadro e quindi fare clic su **eliminare**.  
  
## Vedere anche  
 [Filtri join](../../../relational-databases/replication/merge/join-filters.md)   
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  
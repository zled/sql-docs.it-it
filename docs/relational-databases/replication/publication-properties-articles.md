---
title: "Propriet&#224; pubblicazione, Articoli | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.articles.f1"
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Propriet&#224; pubblicazione, Articoli
  Il **articoli** pagina la **Proprietà pubblicazione** la finestra di dialogo: contiene informazioni sugli articoli contenuti in una pubblicazione, consente di aggiungere o eliminare gli articoli da pubblicazioni esistenti, e consente di modificare le proprietà di articolo e filtro di colonna.  
  
> [!NOTE]  
>  Dopo la creazione di una pubblicazione, per alcune modifiche delle proprietà è necessario un nuovo snapshot. Se la pubblicazione dispone di sottoscrizioni, per alcune modifiche è inoltre necessario reinizializzare tutte le sottoscrizioni. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../relational-databases/replication/publish/change-publication-and-article-properties.md) e [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
 Se si pubblica un oggetto di database che dipende da uno o più oggetti di database diversi, è necessario pubblicare tutti gli oggetti a cui si fa riferimento. Se ad esempio si pubblica una vista che dipende da una tabella, sarà necessario pubblicare anche la tabella.  
  
 Accanto agli oggetti che non possono essere pubblicati viene visualizzata un'icona rossa con una spiegazione nel pannello informativo nella parte inferiore della pagina della procedura guidata. Non è possibile pubblicare gli oggetti seguenti:  
  
-   Oggetti crittografati.  
  
-   Viste indicizzate contenenti colonne che consentono l'uso di valori NULL.  
  
-   Le tabelle prive di chiavi primarie non possono essere pubblicate nelle pubblicazioni transazionali.  
  
-   Le tabelle non possono essere pubblicate in una pubblicazione di tipo merge né in una pubblicazione transazionale abilitata per le sottoscrizioni ad aggiornamento in coda. Per ulteriori informazioni sulla pubblicazione di un articolo in più pubblicazioni, vedere la sezione "Pubblicazione le tabelle in più pubblicazioni" [pubblicare dati e oggetti di Database](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
## Server di pubblicazione Oracle  
 Per i server di pubblicazione Oracle, sono disponibili indicazioni aggiuntive:  
  
-   Per un elenco di oggetti che possono essere pubblicati da Oracle, vedere [Considerazioni sulla progettazione e limitazioni per server di pubblicazione Oracle](../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md). Gli oggetti che non possono essere pubblicati non vengono visualizzati.  
  
-   Per un elenco di tipi di dati che possono essere pubblicati, vedere [Mapping di tipi di dati per server di pubblicazione Oracle](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md). Le colonne contenenti tipi di dati che non possono essere pubblicati non vengono visualizzate.  
  
## Filtri colonne  
 Filtrare le colonne in questa pagina espandendo una tabella di **oggetti da pubblicare** riquadro e quindi selezionando solo le colonne richieste (righe possono essere filtrate nel **filtro righe tabella** pagina della procedura guidata). L'applicazione di un filtro alle colonne è utile per diversi motivi, inclusi motivi di sicurezza, ovvero per impedire la replica dei dati sensibili, e di prestazione, ad esempio per evitare la replica di colonne contenenti dati BLOB (Binary Large Object). Per ulteriori informazioni sul filtro di colonna, incluso un elenco di tipi di colonna non può essere filtrato, vedere [filtrare i dati pubblicati](../../relational-databases/replication/publish/filter-published-data.md).  
  
## Opzioni  
 Il **oggetti da pubblicare** riquadro consente di:  
  
-   Visualizzare tutti gli oggetti disponibili per la replica.  
  
-   Aggiungere un articolo a una pubblicazione selezionando la casella di controllo accanto a tale oggetto.  
  
-   Rimuovere un articolo da una pubblicazione deselezionando la casella di controllo accanto a tale oggetto. Per informazioni su quando gli articoli possono essere eliminati, vedere [eliminare articoli da pubblicazioni esistenti e aggiungere articoli alla](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Includere tutti gli oggetti di un determinato tipo (ad esempio una tabella) nella pubblicazione selezionando la casella di controllo accanto a tale tipo di oggetto (ad esempio **tabelle**).  
  
-   Espandere tutti i nodi della tabella per visualizzarne le relative colonne.  
  
-   Escludere tramite un filtro le colonne della tabella dalla pubblicazione deselezionando la casella di controllo accanto alla colonna oppure includere le colonne non pubblicate selezionando la casella di controllo.  
  
-   Fare clic con il pulsante destro del mouse su un oggetto nel riquadro per visualizzare un menu di comandi per tale oggetto.  
  
 **Proprietà articolo**  
 Fare clic su **Proprietà articolo** , quindi fare clic su uno dei seguenti:  
  
-   Fare clic su **impostare proprietà di evidenziate \< ObjectType> articolo** per avviare il **Proprietà articolo - \< ObjectName>** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate solo all'oggetto evidenziato nel riquadro degli oggetti nel **articoli** pagina.  
  
-   Fare clic su **impostare le proprietà di tutti \< ObjectType> articoli**, per avviare il **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate a tutti gli oggetti di quel tipo nel riquadro degli oggetti nel **articoli** pagina, inclusi quelli non ancora selezionati per la pubblicazione.  
  
    > [!NOTE]  
    >  Modifiche delle proprietà apportate nel **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo sostituire qualsiasi apportate in precedenza il **Proprietà articolo - \< ObjectName>** la finestra di dialogo. Se ad esempio si desidera impostare alcuni valori predefiniti per tutti gli articoli di un tipo di oggetto e, al contempo, alcune proprietà per singoli oggetti, è necessario impostare innanzitutto i valori predefiniti per tutti gli articoli, quindi le proprietà relative ai singoli oggetti.  
  
 **La tabella evidenziata è di tipo solo download**  
 Solo per la replica di tipo merge. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Selezionare questa opzione per indicare che non è possibile apportare modifiche nel Sottoscrittore se si utilizza una sottoscrizione client. Poiché non è possibile aggiornare gli articoli di solo download nel Sottoscrittore, i metadati di rilevamento non vengono inviati ai Sottoscrittori. Ciò può comportare uno spazio di archiviazione ridotto sui Sottoscrittori e un vantaggio in termini di prestazioni, soprattutto se la connessione di rete è lenta. Questa opzione corrisponde a un valore di **solo Download sul sottoscrittore, non consentire modifiche del sottoscrittore** per l'opzione **la direzione di sincronizzazione** nel **Proprietà articolo** la finestra di dialogo. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Mostra solo oggetti selezionati nell'elenco**  
 Selezionare questa casella di controllo per visualizzare solo gli articoli selezionati nel riquadro degli oggetti.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
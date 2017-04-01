---
title: "Propriet&#224; pubblicazione, Filtra righe | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.filterrows.f1"
ms.assetid: 2c5fdbed-9b10-4818-98cc-cc6b01351318
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propriet&#224; pubblicazione, Filtra righe
  Il **Filtra righe** pagina della **Proprietà pubblicazione** finestra di dialogo consente di aggiungere, modificare o eliminare:  
  
-   Applicare filtri di riga statici agli articoli di tabella nelle pubblicazioni snapshot, transazionali e di tipo merge.  
  
-   Applicare filtri di riga con parametri agli articoli di tabella nelle pubblicazioni di tipo merge.  
  
-   Utilizzare filtri join per estendere i filtri degli articoli di tabelle di merge agli articoli di tabelle correlate.  
  
 Per ulteriori informazioni sulle opzioni di filtro, vedere [filtrare i dati pubblicati](../../relational-databases/replication/publish/filter-published-data.md).  
  
> [!NOTE]  
>  Per aggiungere, modificare o eliminare un filtro sono necessari un nuovo snapshot per la pubblicazione e la reinizializzazione di tutte le sottoscrizioni.  
  
 Per ottimizzare le prestazioni dell'applicazione e ridurre la quantità di spazio di archiviazione necessario o per limitare la disponibilità di determinati dati a Sottoscrittori specifici, è consigliabile pubblicare solo i dati necessari. La pubblicazione può includere sia tabelle filtrate che tabelle non filtrate. È possibile ad esempio includere la tabella completa, non filtrata, dei prodotti della società e utilizzare i filtri di riga per generare una tabella filtrata dei clienti di una regione specifica. Tramite l'applicazione di filtri ai dati pubblicati è possibile:  
  
-   Ridurre al minimo la quantità di dati inviati in rete.  
  
-   Ridurre la quantità di spazio di archiviazione necessaria nel Sottoscrittore.  
  
-   Personalizzare le pubblicazioni e le applicazioni in base ai requisiti dei singoli Sottoscrittori.  
  
-   Evitare o limitare i conflitti in caso di aggiornamento dei dati da parte dei Sottoscrittori grazie alla possibilità di inviare partizioni di dati diverse a Sottoscrittori diversi. In due Sottoscrittori pertanto non verranno mai aggiornati gli stessi valori di dati.  
  
-   Evitare la trasmissione di dati riservati. È possibile utilizzare i filtri di riga e di colonna per limitare l'accesso ai dati da parte dei Sottoscrittori. Nella replica di tipo merge è necessario tenere in considerazione alcuni aspetti relativi alla sicurezza se si utilizza un filtro con parametri che include HOST_NAME(). Per ulteriori informazioni, vedere la sezione "Applicazione di filtri con HOST_NAME ()" in [i filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Opzioni  
 **Tabelle filtrate**  
 Questo riquadro viene popolato di filtri mano a mano che vengono aggiunti agli articoli di tabella nella pubblicazione. Le tabelle con filtri di riga vengono visualizzate nel riquadro come nodi di livello principale. Per le pubblicazioni di tipo merge, le tabelle alle quali sono stati estesi i filtri tramite un filtro di join vengono visualizzate come nodi figlio.  
  
 **Aggiungi**  
 Fare clic su **Aggiungi** per avviare una finestra di dialogo che consente di filtrare gli articoli di tabella. Fare clic su **Aggiungi** per una pubblicazione snapshot o transazionale avvia immediatamente una finestra di dialogo. Fare clic su **Aggiungi** per un'operazione di unione verranno visualizzate tre opzioni di pubblicazione: **Aggiungi filtro**; **Aggiungi Join per estendere il filtro selezionato**; **Genera filtri automaticamente**.  
  
-   Selezionare **Aggiungi filtro** per avviare il **Aggiungi filtro** la finestra di dialogo. che consente di applicare i filtri di riga a un articolo di tabella. Nel **Aggiungi filtro** nella finestra di dialogo è possibile, ad esempio, specificare che una tabella con dati del cliente deve contenere solo dati sui clienti francesi quando viene replicata ai sottoscrittori.  
  
-   Selezionare **Aggiungi Join per estendere il filtro selezionato** per avviare il **Aggiungi Join** la finestra di dialogo. Il **Aggiungi Join** la finestra di dialogo consente di estendere un filtro di riga in modo che filtri i dati nelle tabelle correlate alla tabella con il filtro di riga. Se, ad esempio, una tabella clienti viene filtrata in modo che contenga solo dati relativi ai clienti francesi ed esiste una tabella correlata per gli ordini dei clienti, è possibile definire un join tra le due tabelle in modo che la tabella degli ordini includa solo gli ordini dei clienti francesi.  
  
    > [!NOTE]  
    >  Questa opzione è disponibile solo selezionando prima la tabella di base del join nel riquadro dei filtri.  
  
-   Selezionare **Genera filtri automaticamente** per avviare il **Genera filtri** la finestra di dialogo. che consente di definire un filtro di riga su una tabella in una pubblicazione di tipo merge che viene automaticamente esteso dalla replica ad altre tabelle correlate tramite relazioni di chiave esterna. Ad esempio, una pubblicazione può includere tre tabelle: una tabella dei clienti, una tabella degli ordini con una chiave esterna alla tabella dei clienti e una tabella dei dettagli degli ordini con una chiave esterna alla tabella degli ordini. Definendo un filtro di riga sulla tabella dei clienti, la replica lo estenderà alle altre tabelle.  
  
    > [!NOTE]  
    >  Se i filtri vengono generati automaticamente dalla replica, qualsiasi filtro esistente per la pubblicazione viene eliminato. Per includere sia i filtri generati automaticamente che i filtri specificati manualmente, generare i filtri prima di specificarne altri. È possibile specificare un solo set di filtri generati automaticamente per ogni pubblicazione.  
  
 **Modifica**  
 Selezionare un filtro di riga o di un filtro di join nel riquadro filtro e fare clic su **Modifica** di avviare il **Modifica filtro** o **Modifica Join** la finestra di dialogo.  
  
 **Delete**  
 Selezionare un filtro di riga o di un filtro di join nel riquadro filtro e fare clic su **eliminare** per eliminare il filtro.  
  
 **Trova tabella**  
 Solo per le pubblicazioni di tipo merge. Fare clic su **Trova tabella** a trovare una tabella in una struttura ad albero di filtro complesse. In un database con relazioni complesse una tabella può essere unita in join a più tabelle e pertanto può apparire in più posizioni all'interno dell'albero di filtro.  
  
 La tabella effettiva appare solo in una posizione all'interno dell'albero, mentre nelle altre posizioni è rappresentata da un collegamento. Un collegamento a una tabella è semplicemente un riferimento alla tabella e non ne visualizza i nodi figlio. Un nodo collegamento è contrassegnato con una freccia di scelta rapida ed espandendo il nodo viene visualizzato il testo **fare clic su Trova tabella per vedere la tabella \< tablename>**.  
  
 Selezionare un nodo collegamento nel riquadro e fare clic su **Trova tabella** il riquadro è espanso e la tabella evidenziata. Se si fa clic su **Trova tabella** senza un nodo collegamento selezionato, un **Trova tabella** viene avviata la finestra di dialogo.  
  
 **Filter**  
 Contiene la definizione [!INCLUDE[tsql](../../includes/tsql-md.md)] del filtro selezionato nel riquadro dei filtri.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtro dei dati pubblicati](../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtri join](../../relational-databases/replication/merge/join-filters.md)   
 [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
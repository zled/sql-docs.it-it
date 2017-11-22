---
title: Recupero di righe | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e3cb9f50806d4796d9f65b05c269f610bd33933
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="fetching-rows"></a>Recupero di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il **IRowset** è l'interfaccia di base del set di righe. Il **IRowset** interfaccia fornisce i metodi per il recupero delle righe in sequenza, recupero dei dati da tali righe e la gestione delle righe. I consumer utilizzano i metodi in **IRowset** per tutte le operazioni di base del set di righe. incluse quelle che consentono di recuperare e rilasciare le righe nonché ottenere i valori delle colonne.  
  
 Quando un consumer Ottiene un puntatore a interfaccia in un set di righe, il primo passaggio consiste in genere per determinare le funzionalità del set di righe utilizzando la **IRowsetInfo:: GetProperties** metodo. In questo modo vengono restituite le informazioni sulle interfacce esposte dal set di righe nonché le funzionalità del set di righe che non vengono visualizzate come interfacce distinte, ad esempio il numero massimo di righe attive e il numero di righe che possono presentare aggiornamenti in sospeso contemporaneamente.  
  
 Il passaggio successivo per i consumer consiste nel determinare le caratteristiche, o metadati, delle colonne nel set di righe. A tale scopo si usa il **IColumnsInfo** metodo per informazioni sulle colonne semplici o **IColumnsRowset** metodo per informazioni sulle colonne estese. Il **GetColumnInfo** metodo restituisce le informazioni seguenti:  
  
-   Il numero di colonne nel set di risultati.  
  
-   Una matrice di strutture DBCOLUMNINFO, una per colonna.  
  
     L'ordine delle strutture corrisponde all'ordine in cui le colonne vengono visualizzate nel set di righe. Ogni struttura DBCOLUMNINFO include metadati di colonna, ad esempio nome della colonna, ordinale della colonna, lunghezza massima consentita per un valore nella colonna, tipo di dati della colonna, precisione e lunghezza.  
  
-   Il puntatore a un archivio per tutti i valori stringa all'interno di un singolo blocco di allocazione.  
  
 Il consumer determina le colonne necessarie dai metadati o in base al comando di testo che ha generato il set di righe. Determina gli ordinali delle colonne necessarie dall'ordinamento delle informazioni di colonna restituite da **IColumnsInfo** o dagli ordinali nel set di righe metadati colonna restituiti da **IColumnsRowset**.  
  
 Il **IColumnsInfo** e **IColumnsRowset** interfacce vengono utilizzate per estrarre informazioni sulle colonne nel set di righe. Il **IColumnsInfo** interfaccia restituisce un set limitato di informazioni, mentre **IColumnsRowset** fornisce tutti i metadati.  
  
> [!NOTE]  
>  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0 e versioni precedenti, la colonna di metadati facoltativa DBCOLUMN_COMPUTEMODE restituita da **IColumnsInfo::** restituisce DBSTATUS_S_ISNULL (anziché i valori che descrivono se la colonna è calcolato) perché non è possibile determinare se la colonna sottostante viene calcolata.  
  
 Gli ordinali vengono utilizzati per specificare un'associazione a una colonna. Un'associazione è una struttura che associa un elemento della struttura del consumer a una colonna. Può inoltre associare il valore dei dati, la lunghezza e il valore dello stato della colonna.  
  
 Un set di associazioni viene raccolto in una funzione di accesso Questo viene creato utilizzando il **IAccessor:: CreateAccessor** metodo. Una funzione di accesso può contenere più associazioni in modo da consentire il recupero o l'impostazione dei dati per più colonne in una singola chiamata. Il consumer può creare diverse funzioni di accesso in base ai differenti modelli di utilizzo nelle varie parti dell'applicazione. Può creare e rilasciare funzioni di accesso mentre il set di righe è ancora attivo.  
  
 Per recuperare righe dal database, il consumer chiama un metodo, ad esempio **IRowset:: GetNextRows** o **IRowsetLocate:: GetRowsAt**. Queste operazioni di recupero inseriscono i dati delle righe dal server nel buffer di riga del provider. Il consumer non dispone di accesso diretto al buffer di riga del provider Il consumer utilizza **IRowset:: GetData** per copiare i dati dal buffer del provider in buffer del consumer e **IRowsetChange:: SetData** per copiare le modifiche dei dati dal buffer del consumer nel buffer del provider.  
  
 Il consumer chiama il **GetData** metodo e passa l'handle per una riga, l'handle per una funzione di accesso e un puntatore a un buffer allocato dal consumer. **GetData** converte i dati e restituisce le colonne come specificato nelle associazioni utilizzate per creare la funzione di accesso. Il consumer può chiamare **GetData** più di una volta per una riga, con diverse funzioni di accesso e i buffer e pertanto il consumer può ottenere più copie degli stessi dati.  
  
 I dati delle colonne a lunghezza variabile possono essere utilizzati in diversi modi. Innanzitutto, tali colonne possono essere associate a una sezione limitata della struttura del consumer. Questo causa il troncamento quando la lunghezza dei dati supera la lunghezza del buffer. Per stabilire se il troncamento si è verificato, il consumer può controllare lo stato DBSTATUS_S_TRUNCATED. Poiché la lunghezza restituita è sempre la lunghezza effettiva in byte, il consumer può determinare anche la quantità di dati troncati.  
  
 Quando il consumer ha terminato il recupero o l'aggiornamento delle righe, viene rilasciato con la **ReleaseRows** metodo. In questo modo vengono rilasciate le risorse dalla copia delle righe nel set di righe e si crea spazio per le nuove righe. Il consumer può quindi ripetere il ciclo di recupero o creazione di righe e di accesso ai dati in esse contenuti.  
  
 Una volta concluso il set di righe, il consumer chiama il **IAccessor:: ReleaseAccessor** metodo per rilasciare le funzioni di accesso. Chiama il **IUnknown:: Release** metodo su tutte le interfacce esposte dal set di righe per rilasciare il set di righe. Quando il set di righe viene rilasciato, forza il rilascio delle eventuali righe o funzioni di accesso rimanenti ancora in gestione da parte del consumer.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Posizione del recupero successivo](../../relational-databases/native-client-ole-db-rowsets/fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  

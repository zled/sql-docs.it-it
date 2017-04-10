---
title: "Risoluzione dei problemi nell&#39;indicizzazione full-text | Microsoft Docs"
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
  - "indici [ricerca full-text]"
  - "risoluzione dei problemi [SQL Server], ricerca full-text"
  - "risoluzione dei problemi [ricerca full-text]"
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
caps.latest.revision: 44
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 43
---
# Risoluzione dei problemi nell&#39;indicizzazione full-text
     
##  <a name="failure"></a> Risoluzione degli errori nell'indicizzazione full-text  
 Durante il popolamento o la gestione di un indice full-text, l'indicizzatore full-text potrebbe non eseguire correttamente l'indicizzazione di una o più righe per i motivi descritti di seguito. Questi errori a livello di riga non impediscono il completamento del popolamento. L'indicizzatore ignora queste righe, pertanto non sarà possibile recuperare il contenuto di tali righe tramite query.  
  
 È possibile che si verifichino errori di indicizzazione nelle situazioni seguenti.  
  
-   Quando l'indicizzatore non è in grado di trovare o caricare un componente filtro o word breaker. Questo errore può verificarsi se la riga della tabella include contenuto o un formato di documento in una lingua non registrata con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure se il componente filtro o word breaker registrato non è stato firmato o non ha superato il controllo della firma durante il caricamento.  
  
-   Quando un componente, ad esempio un word breaker o un filtro, restituisce un errore all'indicizzatore. Questa situazione può verificarsi se il documento indicizzato è danneggiato e il filtro non è in grado di estrarre il testo del documento oppure quando un componente non è in grado di gestire il contenuto di una singola riga oltre una determinata dimensione, a causa di limiti di memoria nell'host del daemon di filtri (fdhost.exe).  
  
 Per ogni errore a livello di riga, nel log di tipo ricerca per indicizzazione vengono inserite informazioni sul motivo dell'errore. Il numero di errori è riepilogato al termine di un popolamento completo o incrementale.  
  
 Esistono altri errori che possono influire sul processo di indicizzazione e impedire il completamento del popolamento.  
  
-   L'indice full-text supera il limite del numero di righe che è possibile inserire in un catalogo full-text.  
  
-   Un indice cluster o un indice di chiave full-text della tabella indicizzata viene danneggiato, eliminato o ricompilato.  
  
-   Un errore hardware o del disco provoca il danneggiamento del catalogo full-text.  
  
-   Un gruppo di file contenente la tabella indicizzata full-text passa alla modalità offline o viene impostato in sola lettura.  
  
 È consigliabile visualizzare il log di tipo ricerca per indicizzazione al termine di tutte le operazioni di popolamento dell'indice full-text significative o quando il popolamento non risulta completato.  
  
### Componenti non firmati  
 Per impostazione predefinita, l'indicizzatore full-text richiede la firma dei filtri e dei word breaker caricati. Se tali componenti non sono firmati, ad esempio in alcuni casi di installazione di componenti personalizzati, è necessario configurare l'indicizzatore full-text in modo che ignori il controllo della firma.  
  
> [!IMPORTANT]  
>  Questa impostazione rende tuttavia l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] meno sicura. È consigliabile firmare tutti i componenti implementati o assicurarsi che tutti i componenti acquistati siano firmati. Per informazioni sulle firme dei componenti, vedere [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
 [Contenuto dell'argomento](#top)  
  
##  <a name="state"></a> Stato incoerente di un indice full-text dopo il ripristino del log delle transazioni  
 Durante il ripristino del log delle transazioni di un database, è possibile che venga visualizzato un avviso che indica che lo stato dell'indice full-text non è coerente. Questo accade perché l'indice full-text di una tabella è stato modificato dopo il backup del database. Per riportare l'indice full-text a uno stato coerente, è necessario eseguire un popolamento completo (ricerca per indicizzazione) della tabella. Per altre informazioni sugli indici full-text, vedere [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md).  
  
 [Contenuto dell'argomento](#top)  
  
## Vedere anche  
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
---
title: "Ottimizzazione delle prestazioni dei filtri con parametri con le partizioni pre-calcolate | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partizioni pre-calcolate [replica di SQL Server]"
  - "partizioni pre-calcolate di replica di tipo merge [replica di SQL Server]"
  - "partizioni pre-calcolate della replica di tipo merge [replica di SQL Server], informazioni"
ms.assetid: 85654bf4-e25f-4f04-8e34-bbbd738d60fa
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Ottimizzazione delle prestazioni dei filtri con parametri con le partizioni pre-calcolate
  Le partizioni pre-calcolate consentono di ottimizzare le prestazioni e possono essere utilizzate con le pubblicazioni di tipo merge filtrate. Rappresentano inoltre un requisito per l'utilizzo dei record logici sulle pubblicazioni filtrate. Per ulteriori informazioni sui record logici, vedere [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Quando viene eseguita la sincronizzazione tra un Sottoscrittore e un server di pubblicazione, quest'ultimo deve valutare i filtri del Sottoscrittore per stabilire quali righe appartengono alla partizione o al set di dati di tale Sottoscrittore. Questo processo di determinazione dell'appartenenza alla partizione delle modifiche apportate nel server di pubblicazione per ogni sottoscrittore che riceve un set di dati filtrato viene definita come *partizione valutazione*. In assenza di partizioni pre-calcolate, la valutazione della partizione deve essere eseguita per ogni modifica apportata a una colonna filtrata nel server di pubblicazione dall'ultima esecuzione dell'agente di merge per uno specifico Sottoscrittore e questo processo deve essere ripetuto per ogni Sottoscrittore sincronizzato con il server di pubblicazione.  
  
 Tuttavia, se il server di pubblicazione e nel Sottoscrittore sono in esecuzione in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva e si utilizzano partizioni pre-calcolate, l'appartenenza alla partizione per tutte le modifiche nel server di pubblicazione viene pre-calcolata e reso persistente nel momento in cui vengono apportate le modifiche. Di conseguenza, quando un Sottoscrittore viene sincronizzato con il server di pubblicazione, può iniziare immediatamente a scaricare le modifiche relative alla propria partizione senza essere sottoposto al processo di valutazione della partizione. In questo modo è possibile ottenere significativi miglioramenti delle prestazioni quando una pubblicazione presenta un numero elevato di modifiche, Sottoscrittori o articoli.  
  
 Oltre a utilizzare partizioni pre-calcolate, creare snapshot preliminari e/o consentire ai Sottoscrittori di richiedere la generazione e l'applicazione di snapshot alla prima sincronizzazione. Utilizzare una o entrambe le opzioni per generare snapshot per le pubblicazioni che utilizzando filtri con parametri. Se non si specifica una di queste opzioni, le sottoscrizioni vengono inizializzate tramite una serie di SELECT e le istruzioni INSERT, anziché utilizzare il **bcp** utilità; questo processo è molto lento. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 **Per utilizzare le partizioni pre-calcolate**  
  
 Per impostazione predefinita, le partizioni pre-calcolate sono abilitate su tutte le pubblicazioni nuove ed esistenti che rispettano le indicazioni descritte sopra. È possibile modificare l'impostazione mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o a livello di programmazione. Per ulteriori informazioni, vedere [ottimizzare i filtri di riga con parametri](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md).  
  
## Requisiti per l'utilizzo delle partizioni pre-calcolate  
 Se vengono soddisfatti i requisiti riportati di seguito, per impostazione predefinita le nuove pubblicazioni di tipo merge vengono create con le partizioni pre-calcolate abilitate e quelle esistenti vengono automaticamente aggiornate per l'utilizzo di tale funzionalità. Se una pubblicazione non soddisfa i requisiti, è possibile modificarla e quindi procedere all'abilitazione delle partizioni pre-calcolate. Se solo alcuni articoli soddisfano questi requisiti, provare a creare due pubblicazioni, abilitandone solo una per le partizioni pre-calcolate.  
  
### Requisiti per le clausole di filtro  
  
-   Le funzioni utilizzate nei filtri di riga con parametri, quali HOST_NAME() e SUSER_SNAME(), devono essere visualizzate direttamente nella clausola di filtro con parametri e non devono essere nidificate all'interno di una vista o di una funzione dinamica. Per ulteriori informazioni su queste funzioni, vedere [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md), [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md), e [i filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   I valori restituiti per ogni Sottoscrittore non devono essere modificati in seguito alla creazione della partizione. Se, ad esempio, si utilizza HOST_NAME() in un filtro, senza sovrascrivere il valore HOST_NAME(), non modificare il nome del computer nel Sottoscrittore.  
  
-   I filtri join non devono contenere funzioni dinamiche, ovvero funzioni come HOST_NAME() e SUSER_SNAME() che restituiscono un valore diverso a seconda del Sottoscrittore in fase di sincronizzazione. Solo i filtri di riga con parametri devono contenere funzioni dinamiche.  
  
-   Non è possibile utilizzare funzioni non deterministiche in una clausola di filtro. Per ulteriori informazioni sulle funzioni non deterministiche, vedere [funzioni deterministiche e non](../../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
-   Le viste a cui viene fatto riferimento nelle clausole relative ai filtri join o ai filtri con parametri non devono contenere funzioni dinamiche.  
  
-   Nella pubblicazione non devono essere presenti relazioni circolari tra filtri join.  
  
### Regole di confronto del database  
  
-   Quando si utilizzano partizioni pre-calcolate, per effettuare confronti vengono sempre utilizzate le regole di confronto del database anziché quelle della tabella o della colonna. Si consideri lo scenario seguente:  
  
    -   Un database con regole di confronto con distinzione tra maiuscole e minuscole contiene una tabella con regole di confronto per le quali non viene applicata tale distinzione.  
  
    -   La tabella contiene una colonna **nomecomputer**, che viene confrontato con il nome host del sottoscrittore in un filtro con parametri.  
  
    -   La tabella contiene una riga con il valore "MYCOMPUTER" e una riga con il valore "mycomputer" in questa colonna.  
  
     Se il Sottoscrittore viene sincronizzato con il nome host "mycomputer", riceverà solo una riga in quanto il confronto supporta la distinzione tra maiuscole e minuscole (le regole di confronto del database). Se le partizioni pre-calcolate non vengono utilizzate, il Sottoscrittore riceverà entrambe le righe, in quanto le regole di confronto della tabella non supportano la distinzione tra maiuscole e minuscole.  
  
## Prestazioni delle partizioni pre-calcolate  
 Il calo delle prestazioni delle partizioni pre-calcolate è ridotto quando le modifiche vengono caricate dal Sottoscrittore nel server di pubblicazione, ma il tempo per l'elaborazione dei processi merge viene impiegato per la valutazione delle partizioni e il download delle modifiche dal server di pubblicazione al Sottoscrittore e pertanto il guadagno netto può risultare ancora significativo. I vantaggi in termini di prestazioni varieranno a seconda del numero di Sottoscrittori che eseguono contemporaneamente la sincronizzazione e del numero di aggiornamenti per sincronizzazione che comportano lo spostamento delle righe da una partizione all'altra.  
  
## Vedere anche  
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  
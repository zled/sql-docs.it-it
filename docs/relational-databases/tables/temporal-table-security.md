---
title: Sicurezza di una tabella temporale | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 02/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60e5d6f6-a26d-4bba-aada-42e382bbcd38
caps.latest.revision: 9
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f73cdc0f3a240e3d4c795fd67c2913b99748de4a
ms.lasthandoff: 04/11/2017

---
# <a name="temporal-table-security"></a>Sicurezza di una tabella temporale
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per comprendere il tema della sicurezza in riferimento alle tabelle temporali, è importante conoscere i principi di sicurezza che riguardano le tabelle temporali. Dopo aver compreso questi principi è possibile procedere approfondendo il tema della sicurezza in relazione alle istruzioni **CREATE TABLE**, **ALTER TABLE**e **SELECT** .  
  
## <a name="security-principles"></a>Principi di sicurezza  
 La tabella seguente descrive i principi di sicurezza che riguardano le tabelle temporali:  
  
|Principio|Descrizione|  
|---------------|-----------------|  
|L'abilitazione/disabilitazione del controllo delle versioni di sistema richiede i privilegi più elevati per gli oggetti interessati|L'abilitazione e disabilitazione di SYSTEM_VERSIONING richiede l'autorizzazione CONTROL sia per la tabella corrente che per quella di cronologia|  
|I dati di cronologia non possono essere modificati direttamente|Quando SYSTEM_VERSIONING è ON, gli utenti non possono modificare i dati di cronologia indipendentemente dalle autorizzazioni effettive per la tabella corrente o di cronologia. Ciò vale sia per le modifiche dei dati che per quelle dello schema.|  
|Per l'esecuzione di query sui dati di cronologia è richiesta l'autorizzazione **SELECT** per la tabella di cronologia|Il fatto che un utente abbia l'autorizzazione **SELECT** per la tabella corrente non significa che abbia l'autorizzazione **SELECT** per la tabella di cronologia.|  
|Il controllo espone le operazioni che influiscono sulla tabella di cronologia in modi specifici:|Il controllo sulla tabella di cronologia acquisisce regolarmente tutti i tentativi diretti di accesso ai dati (indipendentemente dal fatto che siano riusciti o meno).<br /><br /> **SELECT** con l'estensione per query temporali mostra che la tabella di cronologia è stata interessata da tale operazione.<br /><br /> Le operazioni**CREATE/ALTER** sulla tabella temporale espongono informazioni che indicano che il controllo delle autorizzazioni viene eseguito anche sulla tabella di cronologia. Il file di controllo conterrà record aggiuntivi per la tabella di cronologia.<br /><br /> Le operazioni DML sulla tabella corrente indicano che la tabella di cronologia è stata interessata, ma additional_info fornisce il contesto necessario (DML risultante da SYSTEM_VERSIONING).|  
  
## <a name="performing-schema-operations"></a>Esecuzione di operazioni sullo schema  
 Quando SYSTEM_VERSIONING è impostato su ON, le operazioni di modifica dello schema sono limitate.  
  
### <a name="disallowed-alter-schema-operations"></a>Operazioni ALTER sullo schema non consentite  
  
|Operazione|Tabella corrente|Tabella di cronologia|  
|---------------|-------------------|-------------------|  
|**DROP TABLE**|Non consentita|Non consentita|  
|**ALTER TABLE…SWITCH PARTITION**|Solo SWITCH IN (vedere [Partizionamento con le tabelle temporali](../../relational-databases/tables/partitioning-with-temporal-tables.md))|Solo SWITCH OUT (vedere [Partizionamento con le tabelle temporali](../../relational-databases/tables/partitioning-with-temporal-tables.md))|  
|**ALTER TABLE…DROP PERIOD**|Non consentita|-|  
|**ALTER TABLE…ADD PERIOD**|-|Non consentita|  
  
## <a name="allowed-alter-table-operations"></a>Operazioni ALTER TABLE consentite  
  
|Operazione|Corrente|Cronologia|  
|---------------|-------------|-------------|  
|**ALTER TABLE…REBUILD**|Consentita (in modo indipendente)|Consentita (in modo indipendente)|  
|**CREATE INDEX**|Consentita (in modo indipendente)|Consentita (in modo indipendente)|  
|**CREATE STATISTICS**|Consentita (in modo indipendente)|Consentita (in modo indipendente)|  
  
## <a name="security-of-the-create-temporal-table-statement"></a>Sicurezza dell'istruzione CREATE TABLE per le tabelle temporali  
  
||Creare una nuova tabella di cronologia|Riutilizzare una tabella di cronologia esistente|  
|-|------------------------------|----------------------------------|  
|Autorizzazione necessaria|Autorizzazione**CREATE TABLE** nel database<br /><br /> Autorizzazione**ALTER** per gli schemi in cui vengono create le tabelle corrente e di cronologia|Autorizzazione**CREATE TABLE** nel database<br /><br /> Autorizzazione**ALTER** per lo schema in cui verrà creata la tabella corrente.<br /><br /> Autorizzazione**CONTROL** per la tabella di cronologia specificata come parte dell'istruzione **CREATE TABLE** per la creazione della tabella temporale|  
|Controllo|Dal controllo risulta che gli utenti hanno tentato di creare due oggetti. L'operazione può non riuscire a causa della mancanza di autorizzazioni per creare una tabella nel database o a causa della mancanza di autorizzazioni per la modifica degli schemi per entrambe le tabelle.|Il controllo indica che la tabella temporale è stata creata. L'operazione può non riuscire a causa della mancanza di autorizzazioni per creare una tabella nel database, a causa della mancanza di autorizzazioni per la modifica dello schema per la tabella temporale o a causa della mancanza di autorizzazioni per la tabella di cronologia.|  
  
## <a name="security-of-the-alter-temporal-table-set-systemversioning-onoff-statement"></a>Sicurezza dell'istruzione ALTER TABLE SET (SYSTEM_VERSIONING ON/OFF) per le tabelle temporali  
  
||Creare una nuova tabella di cronologia|Riutilizzare una tabella di cronologia esistente|  
|-|------------------------------|----------------------------------|  
|Autorizzazione necessaria|Autorizzazione**CONTROL** nel database<br /><br /> Autorizzazione**CREATE TABLE** nel database<br /><br /> Autorizzazione**ALTER** per gli schemi in cui viene creata la tabella di cronologia|Autorizzazione**CONTROL** per la tabella originale modificata<br /><br /> Autorizzazione**CONTROL** per la tabella di cronologia specificata come parte dell'istruzione **ALTER TABLE** |  
|Controllo|Il controllo indica che la tabella temporale è stata modificata e contemporaneamente è stata creata la tabella di cronologia. L'operazione può non riuscire a causa della mancanza di autorizzazioni per creare una tabella nel database, a causa della mancanza di autorizzazioni per la modifica dello schema per la tabella di cronologia o a causa della mancanza di autorizzazioni per la modifica della tabella temporale.|Il controllo indica che la tabella temporale è stata modificata, ma l'operazione ha richiesto l'accesso alla tabella di cronologia. L'operazione potrebbe non riuscire a causa della mancanza di autorizzazioni per la tabella di cronologia o per la tabella corrente.|  
  
## <a name="security-of-select-statement"></a>Sicurezza dell'istruzione SELECT  
 L'autorizzazione**SELECT** è invariata per le istruzioni **SELECT** senza effetti sulla tabella di cronologia. Per le istruzioni **SELECT** che interessano la tabella di cronologia, l'autorizzazione **SELECT** è richiesta sia per la tabella corrente che per la tabella di cronologia.  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Security%20page)  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)   
 [Introduzione alle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Verifiche di coerenza del sistema della tabella temporale](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Partizionamento con le tabelle temporali](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Considerazioni e limitazioni delle tabelle temporali](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Funzioni e viste per i metadati delle tabelle temporali](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  


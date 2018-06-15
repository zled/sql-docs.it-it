---
title: 'Novità di sistema della piattaforma Analitica: scalabilità orizzontale data warehouse'
description: Novità di Microsoft® Analitica piattaforma del sistema, uno strumento di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse, vedere.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2408e84e7ff81f54ad00a98f85cd8dce7b04131
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34550642"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Novità nel sistema della piattaforma Analitica, un data warehouse di scalabilità orizzontale MPP
Vedere Novità gli ultimi aggiornamenti di dispositivo per Microsoft® Analitica Platform System (AP). Punti di accesso è uno strumento di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse. 


## <a name="aps-au7"></a>AU7 APS
APS2016 è un prerequisito necessario per eseguire l'aggiornamento a AU7. Di seguito sono le nuove funzionalità per APS AU7:

### <a name="auto-create-and-auto-update-statistics"></a>Creazione automatica e l'aggiornamento automatico statistiche
APS AU7 crea e aggiorna le statistiche automaticamente, per impostazione predefinita. Per aggiornare le impostazioni delle statistiche, gli amministratori possono utilizzare una nuova voce di menu funzionalità commutatore nel [Configuration Manager](appliance-configuration.md#CMTasks). Il [opzione della funzionalità](appliance-feature-switch.md) controlla la auto-create, l'aggiornamento automatico e il comportamento di aggiornamento asincrono delle statistiche. È inoltre possibile aggiornare le impostazioni delle statistiche con il [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) istruzione.

### <a name="t-sql"></a>T-SQL
Selezionare @var è ora supportato. Per altre informazioni, vedere [selezionare variabile locale] (/ sql/t-sql/language-elements/select-local-variable-transact-sql) 

Hint per la query HASH e gruppo di ordini sono ora supportati. Per altre informazioni, vedere [Hints(Transact-SQL) - Query] (/ / t-sql/query/hint-transact-sql-query sql)

### <a name="feature-switch"></a>Opzione della funzionalità
APS AU7 introduce funzionalità commutatore in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled DmsProcessStopMessageTimeoutInSeconds sono ora e opzioni configurabili che possono essere modificate dagli amministratori.

### <a name="known-issues"></a>Problemi noti
Con il software di APS AU7, siamo sui pacchetti e fornendo l'aggiornamento del BIOS Intel che corregge "attacchi al canale laterale esecuzione speculativo" (noto anche come. Vulnerabilità Spectre e Meltdown). Anche se nello stesso pacchetto, l'aggiornamento del BIOS viene installato manualmente e non fa parte del software APS AU7 installare. Si consiglia di tutti i clienti a installare l'aggiornamento del BIOS. Microsoft è misurato l'effetto del Kernel virtuale indirizzo Shadowing (KVAS), Kernel pagina tabella di riferimento indiretto (KPTI) e stima ramo indiretta attenuazione (IBP) in vari carichi di lavoro SQL in vari ambienti e ha rilevato una riduzione significativa su alcuni carichi di lavoro. È consigliabile testare l'effetto sulle prestazioni dell'abilitazione dell'aggiornamento del BIOS prima di distribuirli in un ambiente di produzione. Se l'effetto sulle prestazioni dell'abilitazione di queste funzionalità è troppo elevato per un'applicazione esistente, è possibile prendere in considerazione se l'Appliance di punti di accesso dal codice non attendibile in esecuzione l'isolamento è una soluzione migliore per l'applicazione. Consultare le informazioni disponibili SQL Server [qui](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

## <a name="aps-2016"></a>2016 APS
Queste sono le nuove funzionalità per APS 2016:

### <a name="sql-server-2016"></a>SQL Server 2016

2016 APS viene eseguita la versione più recente di SQL Server 2016 e utilizza il livello di compatibilità database 130 predefinito.  SQL Server 2016 rende possibile per supportare alcune delle nuove funzionalità, ad esempio gli indici secondari per gli indici columnstore cluster e Kerberos per PolyBase. 


### <a name="t-sql"></a>T-SQL
APS 2016 supporta questi miglioramenti di compatibilità di T-SQL.  Questi elementi del linguaggio aggiuntivi semplificano la migrazione da SQL Server e altre origini dati. 

- [Regole di confronto SQL a livello di colonna][] sono ora supportati oltre alle regole di confronto di Windows.
- [Indici non cluster in indici columnstore cluster][] migliorare le prestazioni delle query che cercano valori specifici in corrispondenza dell'indice columnstore cluster. 
- [SELECT...INTO][] 
- [sp_spaceused()][] consente di visualizzare lo spazio su disco utilizzato o riservato in una tabella o database.
- [Tabelle estese in larghezza][] supporto è quella di SQL Server 2016. Il limite di 32 KB precedente per le dimensioni di riga non esiste più. 

**Tipi di dati**

- [Varchar (max)][], [nvarchar (max)][] e [varbinary (max)][]. Questi tipi di dati LOB hanno una dimensione massima di 2 GB. Per caricare questi oggetti di uso [bcp Utility][]. Polybase e dwloader non supportano questi tipi di dati. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][] e tipi di dati decimale.

**Funzioni finestra**

- [ROWS o RANGE][] nella clausola OVER dell'istruzione SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Funzioni di sicurezza**

- [CHECKSUM()][] e [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Funzioni aggiuntive**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>Miglioramenti di PolyBase, Hadoop

- Compatibilità con Hortonworks HDP 2.4 e HDP 2.5
- Supporto per Kerberos tramite le credenziali con ambito database
- Supporto delle credenziali con il BLOB di archiviazione di Azure

### <a name="install-and-upgrade-enhancements"></a>Installazione e i miglioramenti di aggiornamento

**Gli aggiornamenti di architettura Enterprise** aggiornamento dispositivo esistente a APS 2016 installa il più recente del firmware e aggiornamenti di driver, inclusi correzioni di sicurezza. 

Un nuovo dispositivo da HPE o DELL include tutti gli aggiornamenti più recenti plus:

- Supporto del processore di generazione più recente (Broadwell)
- Aggiornare DDR4 DIMM
- Miglioramento della velocità effettiva DIMM

**Integrazione di**

- Completamente il supporto del nome di dominio completo (FQDN) rende possibile configurare un trust di dominio al dispositivo. 
- Per usare il FQDN, è necessario eseguire un aggiornamento completo e registrarsi durante l'aggiornamento. 

**Tempi di inattività ridotti** installazione o l'aggiornamento a APS 2016 sono più veloce e richiede meno tempo di inattività rispetto alle versioni precedenti. Per ridurre i tempi di inattività, l'installazione o l'aggiornamento: 

 - Semplifica l'applicazione degli aggiornamenti WSUS mediante un'immagine che contiene tutti gli aggiornamenti fino a giugno 2016
 - Si applica gli aggiornamenti della sicurezza con gli aggiornamenti di driver e firmware
 - Posiziona gli ultimi aggiornamenti rapidi e l'utilità di verifica del dispositivo (PAV) del dispositivo in modo che siano pronti per l'installazione senza la necessità di scaricarli.


<!--MSDN references-->
[database compatibility level 130]:/sql/t-sql/statements/alter-database-transact-sql-compatibility-level
[Regole di confronto SQL a livello di colonna]:/sql/relational-databases/collations/collation-and-unicode-support
[Indici non cluster in indici columnstore cluster]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR (MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR (MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY (MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Tabelle estese in larghezza]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp Utility]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS o RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  



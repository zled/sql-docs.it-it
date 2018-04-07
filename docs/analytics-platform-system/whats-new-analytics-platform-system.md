---
title: 'Novità di sistema della piattaforma Analitica: scalabilità orizzontale data warehouse'
author: happynicolle
ms.author: nicw;barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Novità di Microsoft® Analitica piattaforma del sistema, uno strumento di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse, vedere.
ms.date: 11/28/2016
ms.topic: article
ms.openlocfilehash: c6af71d6b7c2bc67aeea0fdc5c1af2e668f537c5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="whats-new-in-analytics-platform-system-2016-a-scale-out-mpp-data-warehouse"></a>Novità di Analitica piattaforma System 2016, un data warehouse di scalabilità orizzontale MPP
Vedere quali sono le novità in Microsoft® Analitica piattaforma di strumenti analitici 2016, l'ultimo aggiornamento del dispositivo per un dispositivo di scalabilità orizzontale in locale che ospita MPP SQL Server Parallel Data Warehouse. 

## <a name="sql-server-2016"></a>SQL Server 2016

2016 APS viene eseguita la versione più recente di SQL Server 2016 e utilizza il livello di compatibilità database 130 predefinito.  SQL Server 2016 rende possibile per supportare alcune delle nuove funzionalità, ad esempio gli indici secondari per gli indici columnstore cluster e Kerberos per PolyBase. 


## <a name="t-sql"></a>T-SQL
APS 2016 supporta questi miglioramenti di compatibilità di T-SQL.  Questi elementi del linguaggio aggiuntivi semplificano la migrazione da SQL Server e altre origini dati. 

- [Regole di confronto a livello di colonna SQL][] sono ora supportati oltre alle regole di confronto di Windows.
- [Indici non cluster in indici columnstore cluster][] migliorare le prestazioni delle query che cercano valori specifici in corrispondenza dell'indice columnstore cluster. 
- [SELECT...INTO][] 
- [sp_spaceused()][] consente di visualizzare lo spazio su disco utilizzato o riservato in una tabella o database.
- [Tabelle estese in larghezza][] supporto è quella di SQL Server 2016. Il limite di 32 KB precedente per le dimensioni di riga non esiste più. 

### <a name="data-types"></a>Tipi di dati

- [Varchar (max)][], [nvarchar (max)][] e [varbinary (max)][]. Questi tipi di dati LOB hanno una dimensione massima di 2 GB. Per caricare questi oggetti di uso [utilità bcp][]. Polybase e dwloader non supportano questi tipi di dati. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERICO][] e tipi di dati decimale.

### <a name="window-functions"></a>Funzioni finestra

- [ROWS o RANGE][] nella clausola OVER dell'istruzione SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

### <a name="security-functions"></a>Funzioni di sicurezza

- [Checksum ()][] e [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

### <a name="additional-functions"></a>Funzioni aggiuntive

- [NEWID()][]
- [RAND()][]

## <a name="polybasehadoop-enhancements"></a>Miglioramenti di PolyBase, Hadoop

- Compatibilità con Hortonworks HDP 2.4 e HDP 2.5
- Supporto per Kerberos tramite le credenziali con ambito database
- Supporto delle credenziali con il BLOB di archiviazione di Azure

## <a name="install-and-upgrade-enhancements"></a>Installazione e i miglioramenti di aggiornamento

### <a name="enterprise-architecture-updates"></a>Aggiornamenti di architettura Enterprise
L'aggiornamento del dispositivo esistente a APS 2016 vengono installati il firmware più recente e gli aggiornamenti di driver, che includono aggiornamenti per la sicurezza. 

Un nuovo dispositivo da HPE o DELL include tutti gli aggiornamenti più recenti plus:

- Supporto del processore di generazione più recente (Broadwell)
- Aggiornare DDR4 DIMM
- Miglioramento della velocità effettiva DIMM

### <a name="integration"></a>Integrazione

- Completamente il supporto del nome di dominio completo (FQDN) rende possibile configurare un trust di dominio al dispositivo. 
- Per usare il FQDN, è necessario eseguire un aggiornamento completo e registrarsi durante l'aggiornamento. 

### <a name="reduced-downtime"></a>Tempo di inattività ridotto
Installazione o l'aggiornamento a APS 2016 è più veloce e richiede meno tempo di inattività rispetto alle versioni precedenti. Per ridurre i tempi di inattività, l'installazione o l'aggiornamento: 

 - Semplifica l'applicazione degli aggiornamenti WSUS mediante un'immagine che contiene tutti gli aggiornamenti fino a giugno 2016
 - Applica aggiornamenti di sicurezza con gli aggiornamenti di driver e firmware
 - Posiziona gli ultimi aggiornamenti rapidi e l'utilità di verifica del dispositivo (PAV) del dispositivo in modo che siano pronti per l'installazione senza la necessità di scaricarli.


<!--MSDN references-->
[database compatibility level 130]:https://msdn.microsoft.com/library/bb510680.aspx
[Regole di confronto a livello di colonna SQL]:https://msdn.microsoft.com/library/ms143726.aspx
[Indici non cluster in indici columnstore cluster]:https://msdn.microsoft.com/library/ms188783.aspx
[Varchar (max)]:https://msdn.microsoft.com/library/ms176089.aspx
[nvarchar (max)]:https://msdn.microsoft.com/library/ms186939.aspx
[varbinary (max)]:https://msdn.microsoft.com/library/ms188362.aspx
[SYSNAME]:https://msdn.microsoft.com/library/ms188021.aspx
[SELECT...INTO]:https://msdn.microsoft.com/library/ms188029.aspx
[sp_spaceused()]:https://msdn.microsoft.com/library/ms188776.aspx
[Tabelle estese in larghezza]:https://msdn.microsoft.com/library/ms143432.aspx
[BULK INSERT]:https://msdn.microsoft.com/library/ms188365.aspx
[utilità bcp]:https://msdn.microsoft.com/library/ms162802.aspx
[UNIQUEIDENTIFIER]:https://msdn.microsoft.com/library/ms187942.aspx
[NUMERICO]:https://msdn.microsoft.com/library/ms187746.aspx
[ROWS o RANGE]:https://msdn.microsoft.com/library/ms189461.aspx
[FIRST_VALUE]:https://msdn.microsoft.com/library/hh213018.aspx
[LAST_VALUE]:https://msdn.microsoft.com/library/hh231517.aspx
[CUME_DIST]:https://msdn.microsoft.com//library/hh231078.aspx
[PERCENT_RANK]:https://msdn.microsoft.com/library/hh213573.aspx
[Checksum ()]:https://msdn.microsoft.com/library/ms189788.aspx
[BINARY_CHECKSUM()]:https://msdn.microsoft.com/library/ms173784.aspx
[HAS_PERMS_BY_NAME()]:https://msdn.microsoft.com/library/ms189802.aspx
[NEWID()]:https://msdn.microsoft.com/library/ms190348.aspx
[RAND()]:https://msdn.microsoft.com/library/ms177610.aspx


  

  



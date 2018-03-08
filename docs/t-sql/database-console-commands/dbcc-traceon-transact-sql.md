---
title: DBCC TRACEON (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_TRACEON_TSQL
- TRACEON
- DBCC TRACEON
- TRACEON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC TRACEON statement
- trace flags [SQL Server], enabling
ms.assetid: 93085324-ebaa-4e38-aac8-5e57b4b0d36d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8c173779833562123c9ba3820fef76bf23b80a43
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-traceon-transact-sql"></a>DBCC TRACEON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Abilita i flag di traccia specificati.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC TRACEON ( trace# [ ,...n ][ , -1 ] ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
*trace#*  
Numero del flag di traccia da abilitare.  
  
*n*  
Segnaposto che indica la possibilità di specificare più flag di traccia.  
  
-1  
Attiva i flag di traccia specificati a livello globale.  
  
WITH NO_INFOMSGS  
Disattiva tutti i messaggi informativi.  
  
## <a name="remarks"></a>Osservazioni  
In un server di produzione, per evitare comportamenti imprevisti è consigliabile abilitare i flag di traccia solo a livello di server mediante uno dei metodi seguenti:
-   Utilizzare il **-T** opzione della riga di comando di avvio di Sqlservr.exe. È una procedura consigliata, in quanto consente di eseguire tutte le istruzioni con il flag di traccia abilitato, inclusi i comandi negli script di avvio. Per altre informazioni, vedere [sqlservr Application](../../tools/sqlservr-application.md).  
-   Utilizzare DBCC TRACEON  **(* * * trace #* [* *,**... *n*]**, -1)** solo quando gli utenti o applicazioni non stanno eseguendo contemporaneamente istruzioni nel sistema.  

I flag di traccia consentono di personalizzare alcune caratteristiche controllando il funzionamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dopo essere stati abilitati, i flag rimangono abilitati nel server fino a quando non vengono disabilitati tramite l'istruzione DBCC TRACEOFF. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili due tipi di flag di traccia: di sessione e globali. I flag di traccia di sessione sono attivi per una connessione e sono visibili solo per tale connessione. I flag di traccia globali vengono impostati a livello del server e sono visibili per tutte le connessioni nel server. Per determinare lo stato dei flag di traccia, eseguire DBCC TRACESTATUS. Per disabilitare i flag di traccia, eseguire DBCC TRACEOFF.
  
Dopo avere attivato un flag di traccia che interessa i piani di query, eseguire `DBCC FREEPROCCACHE;` in modo che i piani memorizzati nella cache vengono ricompilati utilizzando il nuovo comportamento relative ai piani.
  
## <a name="result-sets"></a>Set di risultati  
 L'istruzione DBCC TRACEON restituisce il set di risultati seguente (messaggio):  
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene disabilitata la compressione hardware per le unità nastro mediante l'attivazione del flag di traccia `3205`. Questo flag viene attivato solo per la connessione corrente.
  
```sql  
DBCC TRACEON (3205);  
GO  
```  
  
Nell'esempio seguente viene attivato il flag di traccia `3205` a livello globale.
  
```sql  
DBCC TRACEON (3205, -1);  
GO  
```  
  
Nell'esempio seguente vengono attivati i flag di traccia `3205` e `260` a livello globale.
  
```sql  
DBCC TRACEON (3205, 260, -1);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEOFF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACESTATUS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)  
[Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
[Abilitare relative ai piani query optimizer comportamento di SQL Server che può essere controllato dal flag di traccia diversi a livello di query specifica](https://support.microsoft.com/kb/2801413)
  
  

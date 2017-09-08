---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Documenti Microsoft
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ba6a519ebcdbbc70bf19ec491539a3b07fb6c85
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Svuota la cache di autenticazione del database contenente informazioni sull'account di accesso e le regole firewall, per il database utente corrente in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Questa informativa non si applica al database master logico, poiché il database master contiene l'archivio fisico per le informazioni sull'account di accesso e le regole del firewall. L'utente che esegue l'istruzione e gli altri utenti attualmente connessi rimangano connessi. (FLUSHAUTHCACHE DBCC non è attualmente supportato per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)
 
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
nessuna.
  
## <a name="remarks"></a>Osservazioni  
La cache di autenticazione esegue una copia di account di accesso e delle regole firewall del server che vengono archiviate nel database master e li inserisce in memoria nel database utente.  Poiché le informazioni relative agli utenti di database indipendente sono già memorizzate nel database utente, gli utenti del database indipendente non fanno parte della cache di autenticazione.
Connessioni attive continuamente al [!INCLUDE[ssSDS](../../includes/sssds-md.md)] richiedono la riautorizzazione (eseguite dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]) almeno ogni 10 ore. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] di input la riautorizzazione tentativi utilizzando la password inviata e nessun utente è obbligatorio. Per motivi di prestazioni quando si reimposta una password in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], la connessione non verrà nuovamente autenticata, anche se la connessione viene reimpostata a causa del pool di connessioni. Questo comportamento è diverso dal comportamento di on-premise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se la password è stata modificata dopo la connessione è stata inizialmente autorizzata, è necessario terminare la connessione e stabilire una nuova connessione utilizzando la nuova password. Un utente con l'autorizzazione KILL DATABASE CONNECTION possa terminare in modo esplicito una connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] utilizzando il [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md) comando.
  
## <a name="permissions"></a>Permissions  
Richiede il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] account amministratore.
  
## <a name="example"></a>Esempio  
L'istruzione seguente consente di cancellare la cache di autenticazione per il database corrente.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  


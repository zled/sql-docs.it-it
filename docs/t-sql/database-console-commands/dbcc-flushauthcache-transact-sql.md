---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e313fac1b1a3db6c9a0caa8eb0434dff1ab22411
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618475"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Svuota la cache di autenticazione del database che contiene le informazioni su account di accesso e regole del firewall per il database utente corrente nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Questa istruzione non si applica al database master logico perché il database master contiene lo spazio fisico di archiviazione per le informazioni su account di accesso e regole del firewall. L'utente che esegue l'istruzione e gli altri utenti attualmente connessi mantengono la connessione. DBCC FLUSHAUTHCACHE non è attualmente supportato per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].
 
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
Nessuna.
  
## <a name="remarks"></a>Remarks  
La cache di autenticazione crea una copia degli account di accesso e delle regole firewall del server archiviati nel database master e li inserisce in memoria nel database utente.  Poiché le informazioni relative agli utenti di database indipendente sono già archiviate nel database utente, gli utenti di database indipendente non fanno parte della cache di autenticazione.
Le connessioni continuamente attive al [!INCLUDE[ssSDS](../../includes/sssds-md.md)] richiedono la riautorizzazione (eseguita dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]) almeno ogni 10 ore. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta la riautorizzazione usando la password inviata originariamente e non richiede alcun input da parte dell'utente. Per motivi di prestazioni, quando si reimposta una password nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)], la connessione non verrà nuovamente autenticata, anche se la connessione viene reimpostata a causa del pool di connessioni. Questo comportamento è diverso da quello dell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se la password è stata cambiata dopo l'autorizzazione iniziale della connessione sarà necessario terminare la connessione e stabilirne una nuova usando la nuova password. Un utente con l'autorizzazione KILL DATABASE CONNECTION può terminare in modo esplicito una connessione al [!INCLUDE[ssSDS](../../includes/sssds-md.md)] usando il comando [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md).
  
## <a name="permissions"></a>Permissions  
Richiede l'account amministratore del [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
## <a name="example"></a>Esempio  
L'istruzione seguente consente di cancellare la cache di autenticazione per il database corrente.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  

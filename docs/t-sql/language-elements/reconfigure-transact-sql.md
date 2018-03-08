---
title: RECONFIGURE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 05/20/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RECONFIGURE
- RECONFIGURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- reconfiguring configuration options
- configuration options [SQL Server], reconfiguring
- updating configuration options
- RECONFIGURE, RECONFIGURE statement
- RECONFIGURE
- RECONFIGURE, WITH OVERRIDE statement
ms.assetid: 2e6e4eeb-b70b-4f45-a253-28ac4e595d75
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 432e5157969a10f36273db3bbd8990fa9e332b68
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="reconfigure-transact-sql"></a>RECONFIGURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna il valore attualmente configurato (il **config_value** colonna il **sp_configure** set di risultati) di un'opzione di configurazione modificato con il **sp_configure** sistema stored procedure. Dato che alcune opzioni di configurazione richiedono un arresto di server e il riavvio per aggiornare il valore attualmente in esecuzione, RECONFIGURE non aggiorna sempre il valore attualmente in esecuzione (la **run_value** colonna il **sp_configure**  set di risultati) per un valore di configurazione modificato.    
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Sintassi    
    
```    
    
RECONFIGURE [ WITH OVERRIDE ]    
```    
    
## <a name="arguments"></a>Argomenti    
 RECONFIGURE    
 Specifica che, se le impostazioni di configurazione non richiedono l'arresto e il riavvio del server, viene aggiornato il valore corrente. RECONFIGURE controlla inoltre che i nuovi valori di configurazione per entrambi i valori non validi (ad esempio, un valore di ordinamento che non esiste in **syscharsets**) o non consigliati. Con le opzioni di configurazione che non richiedono l'arresto e il riavvio del server, dopo avere specificato RECONFIGURE il valore corrente e il valore attualmente configurato per l'opzione di configurazione dovrebbero coincidere.    
    
 WITH OVERRIDE    
 Il valore di configurazione per il controllo (per i valori non validi o non consigliati) disabilita il **intervallo di recupero** opzione di configurazione avanzata.    
    
 Qualsiasi opzione di configurazione può essere riconfigurate tramite l'opzione WITH OVERRIDE, tuttavia alcune irreversibili ancora non sono consentiti. Ad esempio, il **memoria del server min** opzione di configurazione non può essere configurato con un valore maggiore di quello specificato nel **la memoria del server max** opzione di configurazione.
      
## <a name="remarks"></a>Osservazioni    
 **sp_configure** non accetta nuovi valori di opzione di configurazione insufficiente nell'intervallo valido per ogni opzione di configurazione.    
    
 L'istruzione RECONFIGURE non è consentita in una transazione esplicita o implicita. Quando si riconfigurano diverse opzioni contemporaneamente, in caso di esito negativo di una o più delle operazioni di riconfigurazione nessuna delle operazioni di riconfigurazione avrà effetto.    
    
 Durante la riconfigurazione di resource governor, vedere l'opzione di RICONFIGURAZIONE di [ALTER RESOURCE GOVERNOR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-resource-governor-transact-sql.md).    
    
## <a name="permissions"></a>Autorizzazioni    
 Le autorizzazioni per RECONFIGURE vengono assegnate per impostazione predefinita agli utenti che dispongono dell'autorizzazione per ALTER SETTINGS. Il **sysadmin** e **serveradmin** ruoli predefiniti del server in modo implicito dispongono di questa autorizzazione.    
    
## <a name="examples"></a>Esempi    
 Nell'esempio seguente viene impostato il limite massimo per l'opzione di configurazione `recovery interval` su `75` minuti e si utilizza `RECONFIGURE WITH OVERRIDE` per la relativa installazione. Gli intervalli di recupero superiori a 60 minuti non sono consigliati e per impostazione predefinita non sono consentiti. Poiché è specificata l'opzione `WITH OVERRIDE`, tuttavia, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non controlla se il valore specificato (`90`) è un valore valido per l'opzione di configurazione `recovery interval`.    
    
```    
EXEC sp_configure 'recovery interval', 75'    
RECONFIGURE WITH OVERRIDE;    
GO    
```    
    
## <a name="see-also"></a>Vedere anche    
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)     
 [sp_configure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)    
    
  

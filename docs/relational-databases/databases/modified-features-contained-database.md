---
title: "Funzionalità modificate (database indipendente) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b44e142fba4e81b90ab7de843bcd8d97ab4ea0c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="modified-features-contained-database"></a>Funzionalità modificate (database indipendente)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le funzionalità seguenti sono state modificate per consentirne il supporto in un database parzialmente indipendente. Le funzionalità vengono generalmente modificate per evitare che superino il limite del database.  
  
 Per altre informazioni, vedere [Database indipendenti](../../relational-databases/databases/contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Livello dell'applicazione  
 In caso di utilizzo dell'istruzione ALTER DATABASE dall'interno di un database indipendente, la sintassi differisce da quella utilizzata per un database non indipendente. Questa differenza include restrizioni di elementi dell'istruzione che si estendono oltre il database fino all'istanza. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
### <a name="instance-level"></a>Livello di istanza  
 Quanto l'istruzione ALTER DATABASE viene utilizzata all'esterno di un database indipendente, la relativa sintassi differisce da quella utilizzata per un database non indipendente. Queste modifiche impediscono di varcare il limite del database. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="create-database"></a>CREATE DATABASE  
 La sintassi di CREATE DATABASE per un database indipendente differisce da quella per un database non indipendente. Per informazioni sui nuovi requisiti della sintassi, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="temporary-tables"></a>Tabelle temporanee  
 All'interno di un database indipendente sono consentite tabelle temporanee locali, ma il relativo comportamento differisce da quelle presenti nei database non indipendenti. Nei database non indipendenti i dati delle tabelle temporanee vengono confrontati nelle regole di confronto di **tempdb**. In un database indipendente i dati delle tabelle temporanee vengono confrontati nelle regole di confronto del database indipendente.  
  
 Tutti i metadati associati alle tabelle temporanee (ad esempio nomi di tabella e di colonna, indici e così via) saranno inclusi nelle regole di confronto del catalogo.  
  
 È possibile che vincoli denominati non vengano utilizzati nelle tabelle temporanee.  
  
 Le tabelle temporanee potrebbero non fare riferimento a tipi definiti dall'utente, raccolte di XML Schema o funzioni definite dall'utente.  
  
## <a name="collation"></a>Confronto  
 Nel modello di database non indipendente sono presenti tre tipi distinti di regole di confronto: del database, dell'istanza e di tempdb. Nei database indipendenti vengono utilizzate solo due regole di confronto, ovvero regole di confronto del database e nuove regole di confronto del catalogo. Per altre informazioni sulle regole di confronto dei database indipendenti, vedere [Regole di confronto dei database indipendenti](../../relational-databases/databases/contained-database-collations.md) .  
  
## <a name="user-options"></a>User Options  
 In caso di abilitazione di database indipendenti, è necessario impostare l'opzione [Opzioni User](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) su 0 per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Regole di confronto dei database indipendenti](../../relational-databases/databases/contained-database-collations.md)   
 [Database indipendenti](../../relational-databases/databases/contained-databases.md)  
  
  

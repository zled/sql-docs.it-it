---
title: Funzionalità modificate (database indipendente) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d08eb0368840a6f2850467d13cbe42c5519c7b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083651"
---
# <a name="modified-features-contained-database"></a>Funzionalità modificate (database indipendente)
  Le funzionalità seguenti sono state modificate per consentirne il supporto in un database parzialmente indipendente. Le funzionalità vengono generalmente modificate per evitare che superino il limite del database.  
  
 Per altre informazioni, vedere [Database indipendenti](contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Livello dell'applicazione  
 In caso di utilizzo dell'istruzione ALTER DATABASE dall'interno di un database indipendente, la sintassi differisce da quella utilizzata per un database non indipendente. Questa differenza include restrizioni di elementi dell'istruzione che si estendono oltre il database fino all'istanza. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
### <a name="instance-level"></a>Livello di istanza  
 Quanto l'istruzione ALTER DATABASE viene utilizzata all'esterno di un database indipendente, la relativa sintassi differisce da quella utilizzata per un database non indipendente. Queste modifiche impediscono di varcare il limite del database. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="create-database"></a>CREATE DATABASE  
 La sintassi di CREATE DATABASE per un database indipendente differisce da quella per un database non indipendente. Per informazioni sui nuovi requisiti della sintassi, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
## <a name="temporary-tables"></a>Tabelle temporanee  
 All'interno di un database indipendente sono consentite tabelle temporanee locali, ma il relativo comportamento differisce da quelle presenti nei database non indipendenti. Nei database non indipendenti i dati delle tabelle temporanee vengono confrontati nelle regole di confronto di **tempdb**. In un database indipendente i dati delle tabelle temporanee vengono confrontati nelle regole di confronto del database indipendente.  
  
 Tutti i metadati associati alle tabelle temporanee (ad esempio nomi di tabella e di colonna, indici e così via) saranno inclusi nelle regole di confronto del catalogo.  
  
 È possibile che vincoli denominati non vengano utilizzati nelle tabelle temporanee.  
  
 Le tabelle temporanee potrebbero non fare riferimento a tipi definiti dall'utente, raccolte di XML Schema o funzioni definite dall'utente.  
  
## <a name="collation"></a>Confronto  
 Nel modello di database non indipendente sono presenti tre tipi distinti di regole di confronto: del database, dell'istanza e di tempdb. Nei database indipendenti vengono utilizzate solo due regole di confronto, ovvero regole di confronto del database e nuove regole di confronto del catalogo. Per altre informazioni sulle regole di confronto dei database indipendenti, vedere [Regole di confronto dei database indipendenti](contained-database-collations.md) .  
  
## <a name="user-options"></a>User Options  
 In caso di abilitazione di database indipendenti, è necessario impostare l'opzione [Opzioni User](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) su 0 per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Regole di confronto dei database indipendenti](contained-database-collations.md)   
 [Database indipendenti](contained-databases.md)  
  
  

---
title: Livelli di isolamento delle transazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0544fe096d75f4dfe64f4501b62948193abaf25a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626849"
---
# <a name="transaction-isolation-levels"></a>Livelli di isolamento delle transazioni
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non garantisce che gli hint di blocco verranno rispettati nelle query che accedono ai metadati tramite viste del catalogo, viste di compatibilità, viste degli schemi delle informazioni e funzioni predefinite di creazione di metadati.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] rispetta internamente solo il livello di isolamento READ COMMITTED per l'accesso ai metadati. Se una transazione utilizza, ad esempio, un livello di isolamento SERIALIZABLE e nella transazione viene eseguito un tentativo di accedere ai metadati utilizzando le viste del catalogo o le funzioni predefinite di creazione di metadati, le query verranno eseguite fino a quando non vengono completate come READ COMMITTED. Nel livello di isolamento dello snapshot, tuttavia, l'accesso ai metadati potrebbe non riuscire a causa di operazioni DDL simultanee. Questo comportamento si verifica perché ai metadati non viene applicato il controllo delle versioni. Per questo motivo, l'accesso agli elementi indicati di seguito nel livello di isolamento dello snapshot potrebbe non riuscire:  
  
-   Viste del catalogo  
  
-   Viste di compatibilità  
  
-   Viste degli schemi delle informazioni  
  
-   Funzioni predefinite di creazione dei metadati  
  
-   Gruppo di stored procedure **sp_help**  
  
-   Stored procedure del catalogo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   Viste e funzioni a gestione dinamica  
  
 Per altre informazioni sui livelli di isolamento, vedere [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 Nella tabella seguente è incluso un riepilogo sull'accesso ai metadati in livelli di isolamento diversi.  
  
|Livello di isolamento|Supportato|Rispettato|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|no|Rispetto non garantito|  
|READ COMMITTED|Sì|Sì|  
|REPEATABLE READ|no|no|  
|SNAPSHOT ISOLATION|no|no|  
|SERIALIZABLE|no|no|  
  
  

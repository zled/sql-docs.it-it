---
title: Sys.trusted_assemblies (Transact-SQL) | Documenti di Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: ''
caps.latest.revision: ''
author: tmullaney
ms.author: thmullan
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a4b98f0bf099a0218d292220e83a81989855ad24
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560151"
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Contiene una riga per ogni assembly attendibili per il server.

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Nome colonna |Tipo di dati |Description |
|--- |--- |--- |
|hash |varbinary(8000 |SHA2_512 l'hash del contenuto dell'assembly. |
|description |nvarchar(4000) |Descrizione definita dall'utente facoltativo dell'assembly. Microsoft consiglia di usare il nome canonico che codifica il nome semplice, numero di versione, impostazioni cultura, chiave pubblica e architettura dell'assembly da considerare attendibile. Questo valore in modo univoco identifica l'assembly sul lato common language runtime (CLR) e lo stesso valore di clr_name in is. |
|create_date |datetime2 |Data che l'assembly è stato aggiunto all'elenco di assembly attendibili. |
|created_by |nvarchar (128) |Nome di account di accesso dell'entità che ha aggiunto l'assembly all'elenco. |
| | | |


## <a name="remarks"></a>Note  

Usa **è necessario aggiungere sp_add_trusted_assembly** e **è necessario aggiungere sys.trusted_assemblies** aggiungere o rimuovere assembly dalla `sys.trusted_assemblies`.

## <a name="see-also"></a>Vedere anche  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


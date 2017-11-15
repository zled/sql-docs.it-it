---
title: Implementazione di IDENTITY in una tabella con ottimizzazione per la memoria | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ff2fc2a470d0382dfe92a91b996b178ee938337
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementazione di IDENTITY in una tabella con ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

IDENTITY è supportato in una tabella ottimizzata per la memoria, purché il valore di inizializzazione e incremento siano entrambi pari a 1 (ovvero l'impostazione predefinita). Le colonne Identity con la definizione di IDENTITY(x, y) dove x != 1 o y != 1 non sono supportate nelle tabelle ottimizzate per la memoria.   
    
Per aumentare il valore di inizializzazione IDENTITY, inserire una nuova riga con un valore esplicito per la colonna Identity, usando l'opzione della sessione `SET IDENTITY_INSERT table_name ON`. Con l'inserimento della riga, il valore di inizializzazione IDENTITY viene cambiato nel valore inserito in modo esplicito più 1. Ad esempio, per aumentare il valore di inizializzazione a 1000, inserire una riga con valore 999 nella colonna Identity. I valori Identity generati inizieranno quindi da 1000.     
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  

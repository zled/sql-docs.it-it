---
title: Implementazione di IDENTITY in una tabella con ottimizzazione per la memoria | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 3e2eac0fd58bccad20094af9eb5956cb14cef54c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055470"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementazione di IDENTITY in una tabella con ottimizzazione per la memoria
  IDENTITY(1, 1) è supportato in una tabella ottimizzata per la memoria. Tuttavia, le colonne Identity con la definizione di IDENTITY(x, y) dove x != 1 o y != 1 non sono supportate nelle tabelle ottimizzate per la memoria. La soluzione alternativa per i valori di identità usa l'oggetto sequenza ([numeri di sequenza](../sequence-numbers/sequence-numbers.md)).  
  
 Rimuovere innanzitutto la proprietà IDENTITY della tabella che si converte in OLTP in memoria. Quindi, definire un nuovo oggetto SEQUENCE per la colonna della tabella. Gli oggetti SEQUENCE come le colonne IDENTITY possono creare valori DEFAULT per le colonne che utilizzano la sintassi NEXT VALUE FOR per ottenere un nuovo valore IDENTITY. Poiché i valori DEFAULT non sono supportati in OLTP in memoria, è necessario passare il valore SEQUENCE appena generato all'istruzione INSERT o a una stored procedure compilata in modo nativo che esegue l'inserimento. Nell'esempio seguente viene illustrato questo modello.  
  
```tsql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 Dopo aver eseguito l'inserimento più volte, nella colonna [c1] vengono visualizzati valori validi a incremento progressivo costante. Questo set di risultati viene generato utilizzando la scansione della tabella e l'indice hash senza `ORDER BY` e quindi le righe non vengono ordinate.  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](migrating-to-in-memory-oltp.md)  
  
  
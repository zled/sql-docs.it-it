---
title: Dopo l'aggiornamento, le parole chiave riservate non possono essere utilizzate come identificatori | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
caps.latest.revision: 10
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bc7569837d0442b23e16c365ea1076b734f23892
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172118"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a>Dopo l'aggiornamento, le parole chiave riservate non possono essere utilizzate come identificatori.
  È stato rilevato l'utilizzo di parole che sono parole chiave riservate. Una parola chiave riservata non può essere utilizzata come identificatore o nome di oggetto a meno che il nome non sia delimitato.  
  
## <a name="component"></a>Componente  
 Motore di database  
  
## <a name="description"></a>Description  
 A livello di compatibilità 90 o inferiore, le parole seguenti non sono parole chiave riservate e possono essere utilizzate come identificatori o nomi di oggetto negli script [!INCLUDE[tsql](../../includes/tsql-md.md)]. A livello di compatibilità 100, tali parole sono parole chiave completamente riservate e non devono essere utilizzate con identificatori o nomi di oggetto.  
  
-   EXTERNAL  
  
-   MERGE  
  
-   PIVOT  
  
-   REVERT  
  
-   STOPLIST  
  
-   TABLESAMPLE  
  
-   UNPIVOT  
  
## <a name="corrective-action"></a>Azione correttiva  
 È consigliabile rinominare l'oggetto. Se questa operazione non può essere eseguita prima dell'aggiornamento, utilizzare uno dei metodi seguenti fino a quando non risulta possibile modificare il nome:  
  
-   Mantenere il livello di compatibilità del database 90 o inferiore.  
  
-   Fare riferimento all'oggetto utilizzando identificatori delimitati. Ad esempio, l'istruzione `CREATE TABLE [MERGE] ([MERGE] int);` utilizza parentesi quadre per delimitare il nome dell'oggetto MERGE.  
  
## <a name="external-resources"></a>Risorse esterne  
 [Parole chiave riservate &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)  
  
 [Identificatori delimitati (motore di Database)](http://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  

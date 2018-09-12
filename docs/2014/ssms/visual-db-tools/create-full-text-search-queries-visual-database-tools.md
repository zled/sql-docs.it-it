---
title: Creare query di ricerca full-text (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 48fd46baa8f64e5e14063c73633e2332146c3ba1
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810537"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Creazione di query di ricerca full-text (Visual Database Tools)
  Nelle ricerche full-text viene utilizzato il predicato CONTAINS per individuare le righe contenenti in una colonna specifica il testo desiderato. Le ricerche full-text possono essere eseguite solo in colonne con indici full-text attivi. Se si tenta di utilizzare la clausola CONTAINS in una colonna che non contiene un indice full-text attualmente attivo, verrà visualizzato un errore. Per altre informazioni sugli indici full-text e la clausola CONTAINS, vedere [ricerca Full-Text](../../relational-databases/search/full-text-search.md) e [contiene &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
### <a name="to-create-a-full-text-search-query"></a>Per creare una query di ricerca full-text  
  
1.  Aprire una query in Esplora soluzioni o crearne una nuova.  
  
2.  Nella clausola WHERE della query utilizzare la funzione CONTAINS per eseguire una ricerca in una colonna di testo completo.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di Query supportati &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Procedure per le query e visualizzazioni di progettazione &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  

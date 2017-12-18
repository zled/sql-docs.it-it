---
title: Creare query di ricerca full-text (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 182b55a1b54b739a67b6ca1443154988fa0ced2b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Creazione di query di ricerca full-text (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Nelle ricerche full-text viene usato il predicato CONTAINS per individuare le righe contenenti il testo desiderato in una colonna specifica. Le ricerche full-text possono essere eseguite solo in colonne con indici full-text attivi. Se si tenta di utilizzare la clausola CONTAINS in una colonna che non contiene un indice full-text attualmente attivo, verrà visualizzato un errore. Per altre informazioni sugli indici full-text e la clausola CONTAINS, vedere [ricerca Full-Text (SQL Server)](http://msdn.microsoft.com/en-us/a0ce315d-f96d-4e5d-b4eb-ff76811cab75) e [CONTAINS (Transact-SQL)](http://msdn.microsoft.com/en-us/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Per creare una query di ricerca full-text  
  
1.  Aprire una query in Esplora soluzioni o crearne una nuova.  
  
2.  Nella clausola WHERE della query utilizzare la funzione CONTAINS per eseguire una ricerca in una colonna di testo completo.  
  
## <a name="see-also"></a>Vedere anche  
[Tipi di query supportati &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Esecuzione di operazioni di base con le query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

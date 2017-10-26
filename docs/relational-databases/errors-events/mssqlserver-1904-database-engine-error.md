---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7f40d48806c181cc12c804bfa5fdf9796f83b77e
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver1904"></a>MSSQLSERVER_1904
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1904|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|KEYCOUNT|  
|Testo del messaggio|Per l'oggetto %S_MSG '%.*ls' nella tabella '%.\*ls' sono presenti %d nomi di colonna nell'elenco chiavi %S_MSG. Il limite massimo per l'elenco delle colonne chiave per indici o statistiche è di %d.|  
  
## <a name="explanation"></a>Spiegazione  
Il numero di colonne chiave nell'elenco per le statistiche o l'indice specificato supera il numero massimo di colonne consentite.  
  
## <a name="user-action"></a>Azione dell'utente  
Modificare l'elenco delle colonne chiave in modo da non includere un numero di colonne superiore a quello specificato.  
  
Per gli indici non cluster, utilizzare la clausola INCLUDE nell'istruzione CREATE INDEX per aggiungere colonne all'indice come colonne non chiave. In questo modo si evita di superare la limitazione relativa alla dimensione di indice corrente che consente al massimo 16 colonne chiave. Per altre informazioni, vedere [Creare indici con colonne incluse](~/relational-databases/indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;Transact-SQL&#41;](~/t-sql/statements/create-statistics-transact-sql.md)  
  


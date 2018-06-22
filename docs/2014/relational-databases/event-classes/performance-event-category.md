---
title: Categoria di eventi Prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 35b8a30db1271f393b9252ed4088a4d628cd4f1e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066463"
---
# <a name="performance-event-category"></a>Categoria di eventi Prestazioni
  Usare la categoria di eventi **Prestazioni** per monitorare le classi di evento **Showplan** e le classi di evento generate in seguito all'esecuzione degli operatori SQL DML (Data Manipulation Language).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento Auto Stats](auto-stats-event-class.md)|Indica un aggiornamento automatico delle statistiche di indice e di colonna.|  
|[Classe di evento Degree of Parallelism &#40;7.0 Insert&#41;](degree-of-parallelism-7-0-insert-event-class.md)|Indica che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stata eseguita un'istruzione SELECT, INSERT, UPDATE o DELETE utilizzando un piano seriale o parallelo. Viene anche riportato il numero di CPU utilizzato per eseguire l'operazione.|  
|[Classe di evento Performance Statistics](performance-statistics-event-class.md)|Esegue il monitoraggio delle prestazioni delle query in esecuzione.|  
|[Classe di evento Showplan All](showplan-all-event-class.md)|Identifica gli operatori **Showplan** in un'istruzione SQL.|  
|[Classe di evento Showplan All for Query Compile](showplan-all-for-query-compile-event-class.md)|Visualizza i dati relativi al tempo di compilazione per gli operatori **Showplan** .|  
|[Classe di evento Showplan Statistics Profile](showplan-statistics-profile-event-class.md)|Visualizza il costo stimato di una query.|  
|[Classe di evento Showplan XML](showplan-xml-event-class.md)|Identifica gli operatori **Showplan** in un'istruzione SQL. La classe di evento archivia ogni evento in un documento XML specifico.|  
|[Classe di evento Showplan XML For Query Compile](showplan-xml-for-query-compile-event-class.md)|Visualizza i dati relativi al tempo di compilazione per gli operatori **Showplan** in formato XML.|  
|[Classe di evento Showplan XML Statistics Profile](showplan-xml-statistics-profile-event-class.md)|Identifica gli operatori **Showplan** associati a un'istruzione SQL. L'output è rappresentato da un documento XML.|  
|[Classe di evento SQL:FullTextQuery](sql-fulltextquery-event-class.md)|Indica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha eseguito una query full-text.|  
|[Classe di evento Plan Guide Successful](plan-guide-successful-event-class.md)|Indica che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato correttamente eseguito un piano di esecuzione per una query o un batch contenente una guida di piano.|  
|[Classe di evento Plan Guide Unsuccessful](plan-guide-unsuccessful-event-class.md)|Indica che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato possibile creare un piano di esecuzione per una query o un batch contenente una guida di piano.|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)  
  
  
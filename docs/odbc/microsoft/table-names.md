---
title: Nomi di tabella | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69af01ea73bfe8ad4f69cb9cae72e8579979ba61
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="table-names"></a>Nomi di tabella
Quando il file dBASE, Microsoft Excel, Paradox, o testo driver viene utilizzato, i nomi di tabella che si verificano nella clausola FROM di SELECT o DELETE, dopo la clausola INTO in istruzioni INSERT e dopo l'aggiornamento, CREATE TABLE e DROP TABLE può contenere un percorso valido, nome del server primario e il nome estensione .  
  
 Utilizzo di un nome di tabella in un' posizione in un'istruzione SQL non supporta l'utilizzo di percorsi o le estensioni, ma accetterà solo il nome primario (ad esempio, EMP da C:\ABC\EMP).  
  
 È possono utilizzare i nomi di correlazione (alias). Ad esempio  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```

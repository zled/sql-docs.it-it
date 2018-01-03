---
title: CREARE l'indice istruzione limitazioni | Documenti Microsoft
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
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3923fdf02d70fe87b0748b7a861cac85ec4b786
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="create-index-statement-limitations"></a>CREARE l'indice istruzione limitazioni
L'istruzione CREATE INDEX non è supportata per i driver Microsoft Excel o testo.  
  
 Un indice può essere definito in un massimo di 10 colonne. Se più di 10 colonne sono inclusi in un'istruzione CREATE INDEX, l'indice non verrà riconosciuto e la tabella verrà considerata come se l'indice non sono stati creati.  
  
 Il driver dBASE non è possibile creare un indice su una colonna LOGICA.  
  
 Quando viene utilizzato il driver dBASE, tempo di risposta nel file di grandi dimensioni può essere migliorata creando un indice (con estensione MDX o ndx) nella colonna (campo) specificato nelle clausole WHERE di un'istruzione SELECT. Gli indici esistenti con estensione MDX verranno applicati automaticamente per =, >, \<, > =, = < e tra gli operatori in una clausola WHERE e predicati LIKE e in predicati di join.  
  
 Quando viene utilizzato il driver dBASE, l'indice creato da un'istruzione CREATE UNIQUE INDEX è in realtà non univoco e possono inserire valori duplicati nella colonna indicizzata. Un solo record da un set con gli stessi valori di chiave può essere aggiunto all'indice.  
  
 Quando viene utilizzato il driver Paradox, è necessario definire un indice univoco su un subset delle colonne in una tabella, incluse la prima colonna contiguo. Impossibile aggiornare una tabella dal driver Paradox se non è definito un indice univoco nella tabella o quando il driver Paradox viene usato senza l'implementazione del motore di Database Borland.

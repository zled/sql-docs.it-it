---
title: MSSQLSERVER_11409 | Microsoft Docs
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
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06919db12a917a28234a88c99f678f5a6b60a933
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|11409|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|ALTERCOL_COLSET_DROP|  
|Testo del messaggio|Impossibile eliminare il set di colonne '%.*ls' nella tabella '%.\*ls' poiché la tabella contiene più di 1025 colonne.|  
  
## <a name="explanation"></a>Spiegazione  
Le tabelle possono contenere un massimo di 1024 colonne non definite come colonne di tipo sparse o calcolate. Quando le colonne di tipo sparse provocano il superamento di 1024 colonne nella tabella, è necessario definire un set di colonne per la tabella. Nella tabella cui viene fatto riferimento sono contenute più di 1024 colonne ed è stato effettuato un tentativo di rimuovere il set di colonne.  
  
## <a name="user-action"></a>Azione dell'utente  
È necessario mantenere il set di colonne con le colonne correnti nella tabella.  
  
Per rimuovere il set di colonne, rimuovere innanzitutto le colonne dalla tabella fino a quando il relativo numero non supera 1024, quindi rimuovere il set di colonne.  
  


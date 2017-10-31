---
title: MSSQLSERVER_511 | Microsoft Docs
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
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6f1ef308a5c84a9c0bdee065c67fcc3328798136
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver511"></a>MSSQLSERVER_511
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|511|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|ROW_TOOBIG|  
|Testo del messaggio|Impossibile creare una riga con dimensioni %d, perché tale valore è maggiore delle dimensioni massime consentite %d.|  
  
## <a name="explanation"></a>Spiegazione  
L'operazione tentata ha provocato il superamento delle dimensioni massime di una riga. rappresentate in genere dal valore 8.060 byte. Alcuni formati di archiviazione contengono overhead che può ridurre le dimensioni della riga disponibili per i dati. Se si utilizzano colonne di tipo sparse, ad esempio, il valore delle dimensioni massime di una riga è di 8.018 byte. Per alcune operazioni che aggiungono o rimuovono righe e per altre che modificano il tipo di dati di una colonna è necessario riscrivere la riga nella pagina di dati, quindi rimuovere riga originale. Per queste operazioni, il limite effettivo alla dimensioni della riga è la metà di quello massimo consentito, poiché la riga originale e quella modificata devono essere contenute entrambe nella pagina di dati per un breve periodo di tempo.  
  
## <a name="user-action"></a>Azione dell'utente  
Se possibile, ridurre le dimensioni della riga.  
  
Se si ritiene che il problema sia causato da un aggiornamento sul posto della riga, è necessario modificare la tabella in più passaggi. Creare una nuova tabella e trasferirvi i dati. Successivamente eliminare la tabella originale e rinominare la nuova tabella oppure troncare la tabella originale, modificarne le righe, quindi spostarvi nuovamente i dati.  
  


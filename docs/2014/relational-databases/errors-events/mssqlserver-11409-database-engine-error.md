---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 587b6d15d37e5259ce911c6d278e2d1b48669bc4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429950"
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
  
  

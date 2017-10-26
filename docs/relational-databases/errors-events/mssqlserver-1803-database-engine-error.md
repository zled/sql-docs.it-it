---
title: MSSQLSERVER_1803 | Microsoft Docs
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
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f14c8fb9f7ec553478ad378764265a13b783a0c5
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1803|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NO_SPACE|  
|Testo del messaggio|Istruzione CREATE DATABASE non riuscita. Per contenere una copia del database modello, il file primario deve essere di almeno %d MB.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea un database eseguendo una copia del database modello. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rinomina quindi la copia e aumenta le dimensioni del nuovo database fino a quelle richieste. In questo caso l'utente ha tentato di creare un database di dimensioni inferiori rispetto al database modello. L'operazione non è riuscita perché le dimensioni del file di dati primario sono minori rispetto a quelle del database modello.  
  
## <a name="user-action"></a>Azione dell'utente  
Creare il database aumentando le dimensioni dei file di database. Ridurre quindi il database se si desidera utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o l'istruzione DBCC SHRINKDATABASE.  
  


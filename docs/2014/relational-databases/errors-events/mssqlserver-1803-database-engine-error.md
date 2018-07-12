---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8472fe5f18515adae38725234a43c130d3108d0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415910"
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
  
  

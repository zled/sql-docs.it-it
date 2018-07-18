---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa4307f1cd72ea797ccf0a607796dca32ef4e1e6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411610"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|5231|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Testo del messaggio|ID oggetto O_ID (oggetto 'NAME'): si è verificato un deadlock durante il tentativo di bloccare questo oggetto per la verifica. L'oggetto è stato ignorato e non verrà elaborato.|  
  
## <a name="explanation"></a>Spiegazione  
 Si è verificato un deadlock durante il tentativo da parte di DBCC di bloccare l'oggetto e DBCC è stato scelto come vittima del deadlock. L'oggetto non verrà elaborato.  
  
## <a name="user-action"></a>Azione dell'utente  
 None  
  
  

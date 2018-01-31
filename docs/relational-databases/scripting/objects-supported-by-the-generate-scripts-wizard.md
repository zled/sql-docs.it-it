---
title: Oggetti supportati dalla procedura guidata di generazione script | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6fddad739f540eaff93834cc7a4f0f6efbcbd500
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Oggetti supportati dalla procedura guidata di generazione script
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] La procedura guidata Genera e pubblica script supporta un subset degli oggetti supportati da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Oggetti supportati  
 Nella tabella seguente vengono elencati gli oggetti pubblicabili supportati dalla procedura guidata Genera e pubblica script.  
  
||||||  
|-|-|-|-|-|  
|Ruolo applicazione|Ruolo del database|schema|Aggregazione definita dall'utente|Visualizzazione*|  
|Assembly|Vincolo DEFAULT|Stored procedure*|Tipo di dati definito dall'utente|Raccolta di XML Schema|  
|Vincolo CHECK|Catalogo full-text|Sinonimo|Funzione definita dall'utente||  
|Stored procedure CLR (Common Language Runtime)*|Indice|Tabella|Tabella definita dall'utente||  
|Funzione CLR definita dall'utente|Regola|Utente**|Tipo definito dall'utente||  
  
 *Pubblicato senza crittografia.  
  
 **Qualsiasi utente non di sistema esistente nel database viene pubblicato come ruolo.  
  
  

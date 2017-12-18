---
title: Oggetti supportati dalla procedura guidata di generazione script | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 87fde29aab8338f096d2132b13011e44fcf96014
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Oggetti supportati dalla procedura guidata di generazione script
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] La procedura guidata Genera e pubblica script supporta un subset degli oggetti supportati da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Oggetti supportati  
 Nella tabella seguente vengono elencati gli oggetti pubblicabili supportati dalla procedura guidata Genera e pubblica script.  
  
||||||  
|-|-|-|-|-|  
|Ruolo applicazione|Ruolo del database|Schema|Aggregazione definita dall'utente|Visualizzazione*|  
|Assembly|Vincolo DEFAULT|Stored procedure*|Tipo di dati definito dall'utente|Raccolta di XML Schema|  
|Vincolo CHECK|Catalogo full-text|Sinonimo|Funzione definita dall'utente||  
|Stored procedure CLR (Common Language Runtime)*|Indice|Tabella|Tabella definita dall'utente||  
|Funzione CLR definita dall'utente|Rule|Utente**|Tipo definito dall'utente||  
  
 *Pubblicato senza crittografia.  
  
 **Qualsiasi utente non di sistema esistente nel database viene pubblicato come ruolo.  
  
  

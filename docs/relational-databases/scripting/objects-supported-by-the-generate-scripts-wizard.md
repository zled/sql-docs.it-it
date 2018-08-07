---
title: Oggetti supportati dalla procedura guidata di generazione script | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6c9c94a2060bcabe012162074bb05ff2fd8fc261
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539751"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Oggetti supportati dalla procedura guidata di generazione script
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La procedura guidata Genera e pubblica script supporta un subset degli oggetti supportati da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
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
  
  

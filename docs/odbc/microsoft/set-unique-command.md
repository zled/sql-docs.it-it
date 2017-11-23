---
title: Comando univoco SET | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6c028638a17d5b6ba98b2d0b9cf41de9549484e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="set-unique-command"></a>Comando univoco SET
Specifica se i record con valori di chiave di indice duplicati vengono mantenuti in un file di indice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 Specifica che tutti i record con un valore di chiave di indice duplicati non essere inclusi nel file di indice. Solo il primo record con il valore di chiave di indice originale è incluso nel file di indice.  
  
 OFF  
 (Predefinito). Specifica che i record con valori di chiave di indice duplicati verranno incluse nel file di indice.  
  
## <a name="remarks"></a>Osservazioni  
 Un file di indice mantiene l'impostazione SET UNIVOCI quando si esegue REINDICIZZAZIONE. Per ulteriori informazioni, vedere [indice](../../odbc/microsoft/index-command.md).

---
title: Comando univoco SET | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbdb92c553b5d4ff3eae3bf0f0c39fa834bcd913
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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

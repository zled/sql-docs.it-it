---
title: Comando TAG DELETE | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cf31107e21cee13d51046e43acc5c557cf20b9ee
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="delete-tag-command"></a>ELIMINARE i comandi di TAG
Rimuove un tag o i tag da un file di indice composto (cdx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argomenti  
 *TagName1*OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]]...  
 Specifica un tag da rimuovere da un file di indice composto. È possibile eliminare più tag con un TAG di eliminare includendo un elenco di nomi di tag separati da virgole. Se due o più tag con lo stesso nome esiste nel file di indice aperto, è possibile rimuovere un tag da un file di indice specifico mediante l'inclusione di *CDXFileName*.  
  
 Tutti i [OF *CDXFileName*]  
 Rimuove tutti i tag da un file di indice composto. Se la tabella corrente include un file di indice composto strutturale, tutti i tag vengono rimosse dal file di indice, il file di indice viene eliminato dal disco e il flag nell'intestazione della tabella che indica la presenza di un file di indice composto strutturale associato viene rimosso. Utilizzare ALL con OF *CDXFileName* per rimuovere tutti i tag da un file di indice composto aprire diverso dal file di indice composto strutturale.  
  
## <a name="remarks"></a>Osservazioni  
 File di indice composto, creati con l'indice contengono tag corrispondenti alle voci di indice. ELIMINARE TAG è utilizzato per rimuovere un tag da file di indice composto aperto. È possibile eliminare solo i tag da file di indice composto aperti nell'area di lavoro corrente. Se si rimuovono tutti i tag da un file di indice composto, il file viene eliminato dal disco.  
  
 Visual FoxPro viene cercato un tag nel file di indice composto strutturale (se aperto). Se il tag non è nel file di indice composto strutturale, Visual FoxPro, cerca i tag degli altri file di indice composto aperto.  
  
## <a name="see-also"></a>Vedere anche  
 [INDEX (comando)](../../odbc/microsoft/index-command.md)

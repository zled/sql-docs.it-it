---
title: Inviare i comandi al Provider di dati sottostante | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a144e0130fec6d62ee55ea68001901815a29fef9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Inviare i comandi al Provider di dati sottostante
Qualsiasi comando che non iniziano con la forma viene passato al provider di dati. Ciò equivale a eseguire un comando shape nel formato "SHAPE {comando provider}". Questi comandi *non* è necessario produrre una **Recordset**. Ad esempio, "forma {DROP TABLE MyTable} è un comando shape valido, presupponendo che il provider di dati supporta DROP TABLE.  
  
 Questa funzionalità consente sia i normali comandi del provider e i comandi di forma per condividere la stessa connessione e transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)

---
title: Inviare i comandi al Provider di dati sottostante | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a2e18440c651a65da820cf2f2d51b00ae98e92d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271950"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Inviare i comandi al Provider di dati sottostante
Qualsiasi comando che non iniziano con la forma viene passato al provider di dati. Ciò equivale a eseguire un comando shape nel formato "SHAPE {comando provider}". Questi comandi *non* è necessario produrre una **Recordset**. Ad esempio, "forma {DROP TABLE MyTable} è un comando shape valido, presupponendo che il provider di dati supporta DROP TABLE.  
  
 Questa funzionalità consente sia i normali comandi del provider e i comandi di forma per condividere la stessa connessione e transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)

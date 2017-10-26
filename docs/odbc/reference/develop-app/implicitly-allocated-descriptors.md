---
title: Allocato implicitamente descrittori | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0746c31b05302eba9cd1fcf4104336ca139b6938
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="implicitly-allocated-descriptors"></a>Descrittori allocati in modo implicito
Quando viene allocato un handle di istruzione, l'applicazione alloca in modo implicito un set di descrittori. L'applicazione può ottenere l'handle di questi allocata in modo implicito i descrittori come attributi dell'handle di istruzione. Quando l'applicazione rilascia l'handle di istruzione, il driver libera tutti i descrittori allocati in modo implicito in tale handle.


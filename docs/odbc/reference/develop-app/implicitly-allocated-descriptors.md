---
title: Allocato implicitamente descrittori | Documenti Microsoft
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
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19e5608b3d0452bfc4274b51fe4ebe76b908ffe9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="implicitly-allocated-descriptors"></a>Descrittori allocati in modo implicito
Quando viene allocato un handle di istruzione, l'applicazione alloca in modo implicito un set di descrittori. L'applicazione può ottenere l'handle di questi allocata in modo implicito i descrittori come attributi dell'handle di istruzione. Quando l'applicazione rilascia l'handle di istruzione, il driver libera tutti i descrittori allocati in modo implicito in tale handle.

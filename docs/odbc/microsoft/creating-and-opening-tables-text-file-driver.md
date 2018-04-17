---
title: Creazione e l'apertura di tabelle (Driver di File di testo) | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 374a234f7c0f9eecc119e36d7dd4305a32745786
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Creazione e l'apertura di tabelle (Driver di File di testo)
Quando viene utilizzato il driver di testo, viene creata una nuova tabella utilizzando il formato specificato in Odbcinst.ini. Se non specificato, le tabelle vengono create nel formato CSVDELIMITED. Per impostazione predefinita, FLOAT colonne predefinito a 22 caratteri e colonne di tipo INTEGER predefiniti di 11 caratteri. Colonne di data e utilizzano il formato AAAA-MM-GG. CHAR e le colonne LONGCHAR sono la larghezza specificata nell'istruzione CREATE.

---
title: Operazioni del cursore libreria | Documenti Microsoft
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
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00469dcf77ae81f5d02765026fe0c1f7194da5d1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-operations"></a>Operazioni di raccolta del cursore
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Se un'applicazione che utilizza un ODBC 2*x* driver effettua chiamate a ODBC 3. *x* libreria di cursori, l'applicazione potrebbe essere in grado di utilizzare ODBC 3. *x* funzionalità non supportate da ODBC 2*x* driver. Un writer dell'applicazione occorre prestare attenzione a come vengono utilizzate queste funzionalità, tuttavia. Utilizzo di ODBC 3. *x* libreria di cursori non rende un ODBC 2*x* driver in un'applicazione ODBC 3. *x* driver.


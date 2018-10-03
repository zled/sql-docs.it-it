---
title: Operazioni della libreria di cursori | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e3fcaf9c83c2613a1dc2df499f11c7df2570ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692399"
---
# <a name="cursor-library-operations"></a>Operazioni della libreria di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzarla nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che utilizzano attualmente questa funzionalità. Microsoft consiglia di usare le funzionalità del driver del cursore.  
  
 Se un'applicazione che utilizza un'API ODBC 2 *. x* driver effettua chiamate a ODBC 3. *x* libreria di cursori, l'applicazione potrebbe essere in grado di utilizzare ODBC 3. *x* le funzionalità che non sono supportate da ODBC 2*x* driver. Un writer dell'applicazione necessario prestare attenzione a come vengono utilizzate queste funzionalità, tuttavia. Utilizzo di ODBC 3. *x* libreria di cursori non rende un ODBC 2 *. x* driver in un'applicazione ODBC 3. *x* driver.

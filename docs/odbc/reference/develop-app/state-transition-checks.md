---
title: Stato di transizione controlli | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23f2b87fc943535075e1456bb31366ff9667b07b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910626"
---
# <a name="state-transition-checks"></a>Controlli delle transizioni di stato
Gestione Driver controlla che lo stato dell'ambiente, connessione o istruzione sia appropriato per la funzione chiamata. Ad esempio, una connessione deve essere un allocato stato quando **SQLConnect** viene chiamato deve essere un'istruzione in una stato quando **SQLExecute** viene chiamato. Gestione Driver restituisce SQL_ERROR per gli errori di transizione di stato.

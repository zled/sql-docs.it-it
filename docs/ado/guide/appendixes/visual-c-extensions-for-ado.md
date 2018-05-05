---
title: Le estensioni di Visual C++ per ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d27cc7776c59364ebc0b69c4872dc8b78ee51116
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-extensions"></a>Estensioni di Visual C++
Il metodo preferito di programmazione di ADO con Visual C++ che utilizza il **#import** direttiva, come descritto in [programmazione ADO in Visual C++](../../../ado/guide/appendixes/visual-c-ado-programming.md). Tuttavia, le versioni precedenti di ADO dotato di un metodo alternativo di programmazione utilizzando Visual C++: estensioni di Visual C++. Questa sezione viene illustrata questa funzionalità per gli utenti che devono gestire il codice di estensioni di Visual C++, ma nuovo codice ADO deve essere scritto utilizzando #**importare**.

 Uno della più difficile processi Visual C++ programmatori faccia durante il recupero dei dati con ADO è la conversione di dati restituito come tipo di dati VARIANT in un tipo di dati C++ e quindi archiviare i dati convertiti in una classe o struttura. Oltre a essere complessa, il recupero di dati C++ tramite un tipo di dati VARIANT riduce le prestazioni.

 ADO fornisce un'interfaccia che supporta il recupero dei dati in tipi di dati C/C++ nativi senza passare attraverso una variante e fornisce anche le macro del preprocessore che semplificano l'uso dell'interfaccia. Il risultato è uno strumento flessibile che è più facile da utilizzare e con prestazioni elevate.

 Uno scenario di client C/C++ comune consiste nell'associare un record in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a una struttura di C/C++ o di una classe che contiene i tipi di C/C++ nativi. Se si utilizza varianti, questo comporta la scrittura di codice di conversione da VARIANT a tipi nativi di C/C++. Estensioni di Visual C++ per ADO assegnate in modo molto più semplice questo scenario per i programmatori Visual C++.

 Vedere gli argomenti seguenti per ulteriori informazioni sulle estensioni di Visual C++ per ADO.

-   [Uso delle estensioni di Visual C++ per ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Intestazione delle estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO con esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>Vedere anche
 [Indice ADO per la sintassi di Visual C++ per COM](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [uso delle estensioni di Visual C++](../../../ado/guide/appendixes/using-visual-c-extensions.md) [intestazione delle estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

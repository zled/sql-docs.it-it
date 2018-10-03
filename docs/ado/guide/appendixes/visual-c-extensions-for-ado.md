---
title: Estensioni di Visual C++ per ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca21e976783a10a738488762e382982e4fd8fd8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747679"
---
# <a name="visual-c-extensions"></a>Estensioni di Visual C++
Il metodo preferito di programmazione ADO in Visual C++ Usa la **#import** direttiva, come descritto in [programmazione ADO in Visual C++](../../../ado/guide/appendixes/visual-c-ado-programming.md). Tuttavia, le versioni precedenti di ADO forniti con un metodo alternativo di programmazione con Visual C++: le estensioni di Visual C++. Questa sezione viene illustrata questa funzionalità per gli utenti che devono mantenere il codice di estensioni di Visual C++, ma nuovo codice ADO deve essere scritto usando &**importare**.

 Tra i più noioso processi Visual C++ ai programmatori affrontati quando il recupero dei dati con ADO converte i dati restituiti come tipo di dati VARIANT in un tipo di dati C++ e quindi archiviare i dati convertiti in una classe o struttura. Oltre a essere un'operazione complessa, il recupero di dati C++ tramite un tipo di dati VARIANT, riduce le prestazioni.

 ADO fornisce un'interfaccia che supporta il recupero dei dati in tipi di dati C/C++ nativi senza passare attraverso una variante e fornisce anche le macro del preprocessore che semplificano l'uso dell'interfaccia. Il risultato è uno strumento flessibile che è più facile da usare e con ottime prestazioni.

 Uno scenario di client C/C++ comune consiste nell'associare un record in una [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a una struttura di C/C++ o di una classe che contiene i tipi nativi C/C++. Quando si esegue varianti, ciò comporta la scrittura di codice di conversione da VARIANT a tipi nativi C/C++. Le estensioni di Visual C++ per ADO sono destinate a rendere molto più semplice questo scenario per i programmatori Visual C++.

 Vedere gli argomenti seguenti per altre informazioni sulle estensioni di Visual C++ per ADO.

-   [Uso delle estensioni di Visual C++ per ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Intestazione delle estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO con esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>Vedere anche
 [Indice sintassi di Visual C++ per COM ADO per](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [usando estensioni di Visual C++](../../../ado/guide/appendixes/using-visual-c-extensions.md) [intestazione delle estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

---
title: Riferimento alle librerie ADO In un'applicazione Visual C++ | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9003a9ac341663127a4b337a1313a50f67d1fe5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Riferimento alle librerie ADO In un'applicazione Visual C++
Per utilizzare la versione più recente di ADO in un'applicazione Visual C++, utilizzare la seguente `#import` direttiva:  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Per utilizzare ADO MD o ADOX, è necessario importare *msadomd* o *Msadox*, utilizzando la sintassi precedente.  
  
## <a name="backward-compatibility"></a>Compatibilità con le versioni precedenti  
 Per utilizzare una versione precedente di ADO, sostituire *msado15.dll* sopra con una delle librerie dei tipi seguenti.  
  
-   *msado27.tlb*, libreria dei tipi 2.7 ADO  
  
-   *msado26.tlb*, ADO 2.6 libreria  
  
-   *msado25.tlb*, libreria dei tipi 2,5 ADO  
  
-   *Msado21*, libreria dei tipi 2.1 ADO  
  
-   *msado20.tlb*, ADO libreria dei tipi 2.0

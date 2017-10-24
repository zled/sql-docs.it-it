---
title: Riferimento alle librerie ADO In un'applicazione Visual C++ | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.prod: sql-non-specified
ms.technology: "“drivers”"
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 44d731d8c9e61c29f1dc9eb0c8ea12d57402639c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
-   *msado26.tlb*, ADO 2.6 libreria di tipi  
  
-   *msado25.tlb*, libreria dei tipi di 2,5 ADO  
  
-   *Msado21*, libreria dei tipi 2.1 ADO  
  
-   *msado20.tlb*, ADO libreria dei tipi 2.0


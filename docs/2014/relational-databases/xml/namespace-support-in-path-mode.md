---
title: Supporto dello spazio dei nomi in modalità di PATH | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f75a1a1281ba482935a264c2e5bdac6e6bb290e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297571"
---
# <a name="namespace-support-in-path-mode"></a>Supporto dello spazio dei nomi in modalità di PATH
  In questa versione, il supporto dello spazio dei nomi in modalità PATH è disponibile utilizzando WITH NAMESPACES. Ad esempio, nella query seguente viene illustrata la sintassi WITH NAMESPACES per la dichiarazione di uno spazio dei nomi ("a:") che è possibile utilizzare nell'istruzione SELECT successiva:  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Esempi  
 In questi esempi viene illustrato l'utilizzo della modalità PATH nella generazione di codice XML da una query SELECT. Molte di queste query vengono specificate sui documenti XML di istruzioni per la produzione di biciclette archiviate nella colonna Instructions della tabella ProductModel.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](use-path-mode-with-for-xml.md)  
  
  

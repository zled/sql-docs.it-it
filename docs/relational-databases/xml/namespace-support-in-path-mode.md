---
title: "Supporto dello spazio dei nomi in modalità di PATH | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 733d1a16e352403ca55053ea45a464591e92d7fb
ms.lasthandoff: 04/11/2017

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
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  

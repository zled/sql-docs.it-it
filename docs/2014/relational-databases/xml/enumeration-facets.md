---
title: Facet di enumerazione | Microsoft Docs
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
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf9f843f840c5f174bafe0dbdd5dff46bf55c4f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227051"
---
# <a name="enumeration-facets"></a>facet di enumerazione
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rifiuta XML Schema con tipi che dispongono di facet basati su pattern o di enumerazioni che violano tali facet.  
  
## <a name="example"></a>Esempio  
 Ad esempio, lo schema seguente verrebbe rifiutato in quanto il valore di enumerazione fornito include un valore con lettere sia maiuscole che minuscole e inoltre viola il valore di pattern che limita i valori esclusivamente alle lettere minuscole.  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per le raccolte di XML Schema nel server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

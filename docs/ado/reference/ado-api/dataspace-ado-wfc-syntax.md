---
title: Spazio dati (ADO - sintassi WFC) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0344190472a9548880e828786bd252bdb17de29b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="dataspace-ado---wfc-syntax"></a>Spazio dati (ADO - sintassi WFC)
Il **createObject** metodo il **DataSpace** classe specifica sia un oggetto business per elaborare le richieste dell'applicazione client (*progid*) e il protocollo di comunicazione e il server (*connessione*). **createObject** restituisce un [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) oggetto che rappresenta il server.  
  
## <a name="package-commswfcdata"></a>pacchetto com.ms. wfc.  
  
### <a name="constructor"></a>Costruttore  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Metodi  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)

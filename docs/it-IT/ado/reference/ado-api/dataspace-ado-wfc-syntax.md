---
title: Spazio dati (ADO - sintassi WFC) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba4746a818dfa85699ac3150ad5b7bccbad746ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
 [Oggetto DataSpace (Servizi Desktop remoto)](../../../ado/reference/rds-api/dataspace-object-rds.md)

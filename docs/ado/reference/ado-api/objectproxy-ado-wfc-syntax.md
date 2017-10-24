---
title: ObjectProxy (ADO - sintassi WFC) | Documenti Microsoft
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
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0bd3aa2bd2cf7b49432e6b29c312e65819d50f4a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - sintassi WFC)
Un **ObjectProxy** oggetto rappresenta un server e viene restituito dal **createObject** metodo il [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto. La classe ObjectProxy include un metodo, **chiamare**, che può richiamare un metodo nel server e restituire un oggetto risultante da tale chiamata.  
  
 **pacchetto com.ms. wfc.**  
  
## <a name="methods"></a>Metodi  
  
### <a name="call-method-adowfc-syntax"></a>Metodo di chiamata (sintassi ADO/WFC)  
 Richiama un metodo sul server rappresentato dall'oggetto ObjectProxy. Facoltativamente, gli argomenti del metodo possono essere passati come una matrice di oggetti.  
  
#### <a name="syntax"></a>Sintassi  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Valori di codice restituiti  
 Oggetto  
 Oggetto risultante dalla chiamata al metodo.  
  
#### <a name="parameters"></a>Parametri  
 *ObjectProxy*  
 Un **ObjectProxy** oggetto che rappresenta il server.  
  
 *metodo*  
 Stringa contenente il nome del metodo da richiamare sul server.  
  
 *argomenti*  
 Facoltativa. Matrice di oggetti che rappresentano argomenti del metodo nel server. Tipi di dati Java vengono automaticamente convertiti in tipi di dati adatti per l'uso nel server.


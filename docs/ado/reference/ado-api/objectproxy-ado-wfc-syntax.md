---
title: ObjectProxy (ADO - sintassi WFC) | Documenti Microsoft
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
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9f30144edb28fb58e6cb2606f24df22fedce613
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - sintassi WFC)
Un **ObjectProxy** oggetto rappresenta un server e viene restituito dal **createObject** metodo il [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto. La classe ObjectProxy include un metodo, **chiamare**, che può richiamare un metodo nel server e restituire un oggetto risultante da tale chiamata.  
  
 **package com.ms.wfc.data**  
  
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
  
 *Metodo*  
 Stringa contenente il nome del metodo da richiamare sul server.  
  
 *argomenti*  
 Facoltativa. Matrice di oggetti che rappresentano argomenti del metodo nel server. Tipi di dati Java vengono automaticamente convertiti in tipi di dati adatti per l'uso nel server.

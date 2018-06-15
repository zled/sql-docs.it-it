---
title: Interfaccia livelli di conformità | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 890684bf513b80cd484f7b15c75a04c38553513b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912046"
---
# <a name="interface-conformance-levels"></a>Livelli di conformità di interfaccia
Lo scopo di livellamento è informare l'applicazione di quali funzionalità sono disponibili a esso dal driver. Uno schema di livellamento basato sulle funzioni non sufficientemente raggiungere questo obiettivo. In ODBC 3. *x*, i driver sono classificati in base alle funzionalità di cui dispongono. La funzionalità di supporto può includere che supporta la funzione. può inoltre includere il supporto di un campo di descrizione, un attributo di istruzione, un valore "Y" per un tipo di informazioni restituito da **SQLGetInfo**e così via.  
  
 Per semplificare la specifica di conformità di interfaccia, ODBC definisce tre livelli di conformità. Per soddisfare un livello di conformità specifico, un driver deve soddisfare tutti i requisiti di tale livello di conformità. Conformità con un determinato livello implica la conformità completa con tutti i livelli inferiori.  
  
 Livelli di conformità non sempre dividere accuratamente il supporto per un elenco specifico di funzioni ODBC, ma specificare funzionalità supportate, come indicato nelle sezioni seguenti. Per fornire il supporto per una funzionalità, un driver necessario supportano alcune o tutte le forme di chiamate ad alcune funzioni ODBC (per ulteriori informazioni, vedere [funzione conformità](../../../odbc/reference/develop-app/function-conformance.md)), l'impostazione di determinati attributi (vedere [attributo conformità ](../../../odbc/reference/develop-app/attribute-conformance.md)) e alcuni campi di descrizione (vedere [descrittore campo conformità](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 L'applicazione individua i livello di conformità di un driver interfaccia connettendosi a un'origine dati e la chiamata **SQLGetInfo** con l'opzione SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 I driver sono disponibili implementare le funzionalità oltre il livello a cui dichiarano conformità completezza. Le applicazioni di individuare qualsiasi tali funzionalità aggiuntive chiamando **SQLGetFunctions** , per determinare quali funzioni ODBC sono presenti, e **SQLGetInfo** (per eseguire una query varie altre funzionalità ODBC).  
  
 Esistono tre livelli di conformità interfaccia ODBC: componenti, livello 1 e Level 2.  
  
> [!NOTE]  
>  Questi livelli di conformità hanno requisiti diversi rispetto ai livelli di conformità di API ODBC con lo stesso nome in ODBC 2*x*. In particolare, tutte le funzionalità di cui è inclusa l'API ODBC 2*x* conformità API livello 1 fanno ora parte del livello di conformità interfaccia di base. Di conseguenza, molti driver ODBC può segnalare la conformità di interfaccia a livello di base.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Conformità di interfaccia Core](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Conformità di interfaccia di livello 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Conformità di interfaccia di livello 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Conformità della funzione](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Conformità dell'attributo](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Conformità del campo descrittore](../../../odbc/reference/develop-app/descriptor-field-conformance.md)

---
title: I provider e i componenti del servizio | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 61232bd2d028c9beb1b5471bb6db0b1c28b7b7e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="service-providers-and-components"></a>Provider di servizi e componenti
I provider di servizi sono componenti che estendono la funzionalità del provider di dati mediante l'implementazione di interfacce estese che non sono supportate in modo nativo dall'archivio dati.  
  
 Accesso universale ai dati fornisce un *architettura dei componenti* che consente di singoli componenti specializzati implementare un set discreto di funzionalità del database o i "servizi" in archivi meno avanzati. Pertanto, anziché forzare ogni archivio dati per fornire la propria implementazione di funzionalità estese oppure impostare applicazioni generiche per implementare la funzionalità di database internamente, componenti del servizio forniscono un'implementazione comune che può essere di qualsiasi applicazione utilizzare quando si accede a qualsiasi archivio dati. Il fatto che alcune funzionalità viene implementata in modo nativo dall'archivio dati e altre tramite componenti generici è trasparente all'applicazione.  
  
 Ad esempio, un cursore del motore, ad esempio [il servizio di cursore per OLE DB](http://msdn.microsoft.com/en-us/57638feb-4ecd-4051-becb-8f828d21cf44), è un componente del servizio che può utilizzare dati da un archivio dati sequenziali e forward-only per produrre dati scorrevoli. Altri provider di servizi comunemente utilizzate da ADO includono il [Microsoft OLE DB Provider di persistenza (Provider di servizi ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (per il salvataggio dei dati in un file), il [Microsoft Data shaping per OLE DB (ADO Service Provider) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (per gerarchica **recordset**) e [Provider Microsoft OLE DB remota (Provider di servizi ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (per richiamare i provider di dati in un computer remoto).  
  
 Per ulteriori informazioni sui provider di servizi e dati, vedere [appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md).

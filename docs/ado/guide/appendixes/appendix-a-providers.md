---
title: 'Appendice a: provider | Documenti Microsoft'
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
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1cc5846114e328cb717b8b9c6d86891e97b41ddf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="appendix-a-data-and-service-providers"></a>Appendice a: dati e provider di servizi
In questa sezione vengono tre tipi di provider: provider di dati, i provider di servizi e componenti del servizio. Provider rientrano in due categorie: quelli che forniscono dati e quelli che forniscono servizi. Oggetto *provider di dati* possiede i propri dati e lo espone in formato tabulare all'applicazione. Oggetto *provider di servizi* incapsula un servizio di creazione e utilizzo di dati, in modo da integrare le funzionalità delle applicazioni ADO. Un provider di servizi può inoltre essere definito un *componente del servizio*, che è necessario collaborare con altri provider di servizi o componenti.

## <a name="data-providers"></a>Provider di dati
 ADO è potente e flessibile perché può connettersi a uno di diversi provider di dati diversi ed esporre il modello di programmazione stesso, indipendentemente dalle caratteristiche specifiche di qualsiasi provider specificato.

 Tuttavia, poiché ogni provider di dati è univoco, come l'applicazione interagisca con ADO sarà leggermente diversi da provider di dati. Le differenze in genere suddivisi in tre categorie:

-   Parametri di connessione nel [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà.

-   [Comando](../../../ado/reference/ado-api/command-object-ado.md) utilizzo dell'oggetto.

-   Specifiche del provider [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) comportamento.

 Dettagli per ogni provider di dati Microsoft attualmente disponibili sono elencati di seguito.

|Area|Argomento|
|----------|-----------|
|Database ODBC|[Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Servizio di indicizzazione Microsoft|[Provider Microsoft OLE DB per servizio di indicizzazione Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Servizio Active Directory|[Provider Microsoft OLE DB per Microsoft Active Directory Service](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Database Microsoft Jet|[Provider OLE DB per Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|database Oracle|[Provider Microsoft OLE DB per Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Pubblicazione su Internet|[Provider Microsoft OLE DB per la pubblicazione su Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|Semplici origini dati|[Provider Microsoft OLE DB semplice](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Proprietà dinamiche specifiche del provider
 Il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insiemi di [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [comando](../../../ado/reference/ado-api/command-object-ado.md), e [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti includono le proprietà dinamiche specifiche per il provider. Queste proprietà forniscono informazioni sulle funzionalità specifiche del provider di là delle proprietà predefinite supportate da ADO.

 Dopo avere stabilito la connessione e la creazione di questi oggetti, utilizzare il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo il **proprietà** raccolta dell'oggetto da ottenere le proprietà specifiche del provider. Consultare la documentazione di provider e [Guida per programmatori OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) per informazioni dettagliate su queste proprietà dinamiche.

## <a name="service-providers"></a>Provider di servizi
 Per utilizzare un provider di servizi, è necessario specificare una parola chiave. È necessario essere consapevoli delle proprietà dinamiche specifiche del provider associata a ogni provider di servizi. Dettagli specifici dei provider elencati per ogni provider di servizi che è attualmente disponibile da Microsoft:

-   [Servizio Microsoft di modifica della forma dei dati per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Provider di persistenza Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Provider di servizi remoti Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Componenti del servizio
 Il [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) componente del servizio integra le funzioni di supporto cursore dei provider di dati. Inoltre, richiede una parola chiave e dispone di proprietà dinamiche.

 Per ulteriori informazioni sui provider OLE DB, vedere [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Comandi del provider
 Per ogni provider elencati di seguito, se le applicazioni consentono agli utenti di immettere istruzioni SQL come comandi del provider, è necessario sempre convalidare l'input dell'utente e prestare attenzione ai tentativi possibili pirata informatico utilizzando istruzioni SQL potenzialmente pericolose, ad esempio `DROP TABLE t1`, come parte dell'input dell'utente.

## <a name="see-also"></a>Vedere anche
 [Comando oggetto (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md) [Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [Provider Microsoft OLE DB per Microsoft Active Directory Servizio](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Provider Microsoft OLE DB per servizio di indicizzazione Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Provider Microsoft OLE DB per Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [Provider Microsoft OLE DB per Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [insieme di proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Recordset Oggetto (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)

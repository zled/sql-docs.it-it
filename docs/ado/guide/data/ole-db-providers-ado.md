---
title: I provider OLE DB (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 6e0488c3-934d-4976-99dc-65c580dc7a3c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d00df80315489c2579646aa4faeafff2b57d8f9
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="ole-db-providers-ado"></a>Provider OLE DB (ADO)
OLE DB definisce un set di interfacce COM per consentire alle applicazioni di un accesso uniforme ai dati archiviati in diverse origini dati. Questo approccio consente a un'origine dati condividere i propri dati tramite le interfacce che supportano la quantità di funzionalità DBMS appropriata per l'origine dati. Per impostazione predefinita, l'architettura ad alte prestazioni di OLE DB è basata sul relativo utilizzo di un modello di servizi flessibili e basato su componenti. Invece di un numero predefinito di livelli intermedi tra l'applicazione e i dati, OLE DB richiede solo il numero di componenti necessari per completare un'attività particolare.  
  
 Ad esempio, si supponga che un utente desidera eseguire una query. Esaminare gli scenari seguenti:  
  
-   I dati risiedono in un database relazionale per cui è attualmente disponibile un driver ODBC ma nessun provider OLE DB nativo: l'applicazione utilizza ADO per comunicare con il Provider OLE DB per ODBC, che quindi carica il driver ODBC appropriato. Il driver passa l'istruzione SQL per il sistema DBMS, che recupera i dati.  
  
-   I dati risiedono in Microsoft SQL Server per cui è disponibile un provider OLE DB nativo: l'applicazione utilizza ADO per comunicare direttamente con il Provider OLE DB per Microsoft SQL Server. Non sono necessari intermediari.  
  
-   I dati risiedono in Microsoft Exchange Server, per il quale non esiste un provider OLE DB, ma non espone un motore di elaborazione delle query SQL: l'applicazione utilizza ADO per comunicare con il Provider OLE DB per Microsoft Exchange e chiama un processore di query OLE DB componente per la gestione delle query.  
  
-   I dati si trovano nel file system NTFS Microsoft in forma di documenti: accesso ai dati utilizzando un provider OLE DB nativo su servizio di indicizzazione Microsoft, che indicizza il contenuto e proprietà dei documenti nel file system per consentire a contenuti efficiente esegue la ricerca.  
  
 In tutti gli esempi precedenti, l'applicazione può eseguire query sui dati. Esigenze dell'utente vengono soddisfatte con un numero minimo di componenti. In ogni caso, i componenti aggiuntivi vengono utilizzati solo se necessario, e vengono richiamati solo i componenti necessari. Il caricamento su richiesta di componenti riutilizzabili e condivisibili contribuisce notevolmente a prestazioni elevate, quando si utilizza OLE DB.  
  
 Provider rientrano in due categorie: quelli che forniscono dati e quelli che forniscono servizi. Un provider di dati possiede i propri dati e lo espone in formato tabulare all'applicazione. Un provider del servizio incapsula un servizio per la produzione e l'utilizzo di dati, in modo da integrare le funzionalità delle applicazioni ADO. Un provider di servizi possa anche essere definito come un componente del servizio, che deve funzionare in combinazione con altri provider di servizi o componenti.  
  
 ADO fornisce coerente, interfaccia a livello superiore per i vari provider OLE DB.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Provider di dati](../../../ado/guide/data/data-providers.md)  
  
-   [Provider di servizi e componenti](../../../ado/guide/data/service-providers-and-components.md)

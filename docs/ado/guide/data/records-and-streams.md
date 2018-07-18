---
title: I record e i flussi | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO]
- streams [ADO], about streams
- records [ADO]
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d083594f9dd54cee0f1c9c70f6fdfe14d32e49a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="records-and-streams"></a>I record e flussi
ADO fornisce attualmente il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto come il mezzo principale per l'accesso alle informazioni nelle origini dati, ad esempio database relazionali. Tuttavia, alcuni provider supportano il [Record](../../../ado/reference/ado-api/record-object-ado.md) e [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti come alternativi o complementari oggetti con cui i dati dai provider possono essere modificati. Per informazioni specifiche sulla **Record** comportamento, vedere la documentazione del provider.  
  
## <a name="records"></a>Record  
 **Record** gli oggetti funzionano essenzialmente come una riga **Recordset**s. Tuttavia, **record** hanno funzionalità limitate rispetto ai **recordset** e dispongono di proprietà e metodi diversi. L'origine dei dati in un **Record** oggetto può essere un comando che restituisce una riga di dati dal provider. Utilizzando **Record** oggetti anziché **Recordset** gli oggetti di ricevere i risultati da una query che restituisce una riga di dati Elimina l'overhead di un'istanza più è complessa **Recordset**  oggetto.  
  
 **Record** oggetti possono essere utilizzato un altro scopo, in particolare con provider per le origini di dati diverso da database relazionali tradizionali, ad esempio il [Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Molte delle informazioni che devono essere elaborate esiste, come tabelle nel database, ma come i messaggi in sistemi di posta elettronica e i file nei sistemi di file più recenti. Il **Record** e **flusso** oggetti facilitano l'accesso alle informazioni archiviate nelle origini diverso da database relazionali.  
  
 Il **Record** oggetto può rappresentare e gestire i dati, ad esempio file e directory in un file system o cartelle e i messaggi in un sistema di posta elettronica. A tale scopo, l'origine per il **Record** può essere la riga corrente di un elemento aperto **Recordset**, un URL assoluto o un URL relativo in combinazione con un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
 In genere, un **Recordset** può essere utilizzato per rappresentare un contenitore o in una gerarchia, ad esempio una cartella o una directory padre. Oggetto **Record** può essere utilizzato per restituire informazioni specifiche relative a un nodo nel contenitore padre, ad esempio un file o il documento. Il motivo principale **record** vengono utilizzati per rappresentare questo tipo di informazioni è che queste origini dati eterogenee. Ciò significa che ogni **Record** potrebbe essere un set diverso e un numero di campi. Tradizionale **recordset** contenente le righe da un database sono omogenee, ovvero che ogni riga ha lo stesso numero e tipo dei campi.  
  
 Per ulteriori informazioni sull'utilizzo di **Record** per l'elaborazione di dati eterogenei dai provider, ad esempio Internet Publishing Provider, vedere [utilizzo di ADO per Internet Publishing](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
## <a name="streams"></a>Flussi  
 Il **flusso** oggetto fornisce i mezzi per leggere, scrivere e gestire un flusso di byte. Questo flusso di byte potrebbe essere testo o binari e di dimensione è limitato solo dalle risorse di sistema. In genere, ADO **flusso** gli oggetti vengono utilizzati per gli scopi seguenti:  
  
-   Per contenere i dati di un **Recordset** salvati in formato XML. Questi flussi XML da salvare **Recordset**s utilizzabile come origine quando si apre un nuovo **Recordset**. Per ulteriori informazioni, vedere [flussi e persistenza](../../../ado/guide/data/streams-and-persistence.md).  
  
-   Per contenere [CommandStreams](../../../ado/reference/ado-api/commandstream-property-ado.md) per essere eseguita nel provider come alternativa alla [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md). Ad esempio, gli Updategram XML utilizzabile come origine per un comando sul provider Microsoft OLE DB per SQL Server.  
  
-   Per ricevere i risultati dal provider in un formato diverso da un **Recordset**, ad esempio i risultati XML dal Provider Microsoft OLE DB per SQL Server. Per ulteriori informazioni, vedere [il recupero dei set di risultati in flussi](../../../ado/guide/data/retrieving-resultsets-into-streams.md).  
  
-   Per includere il testo o byte che costituiscono un file o un messaggio, in genere utilizzata con i provider, ad esempio il Provider Microsoft OLE DB per Internet Publishing. Per ulteriori informazioni su questo utilizzo di **flusso** degli oggetti, vedere [utilizzo di ADO per Internet Publishing](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
 Oggetto **flusso** oggetto può essere aperto su:  
  
-   Un semplice file specificato con un URL.  
  
-   Un campo di un **Record** o **Recordset** contenente un **flusso** oggetto.  
  
-   Il flusso predefinito di un **Record** o **Recordset** oggetto che rappresenta una directory o un file composto.  
  
-   Un campo delle risorse contenente l'URL di file semplice.  
  
-   Nessuna origine particolare. In questo caso, un **flusso** oggetto viene aperto in memoria. Dati possono essere scritti in essa e quindi salvati in un altro **flusso** o file.  
  
-   Un campo BLOB in un **Recordset**.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Flussi e persistenza](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [Flussi di comandi](../../../ado/guide/data/command-streams.md)  
  
-   [Recupero di set di risultati nei flussi](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [Uso di ADO per Internet Publishing](../../../ado/guide/data/using-ado-for-internet-publishing.md)

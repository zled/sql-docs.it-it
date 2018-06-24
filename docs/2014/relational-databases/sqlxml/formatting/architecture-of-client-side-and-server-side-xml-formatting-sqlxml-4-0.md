---
title: Architettura della formattazione (SQLXML 4.0) XML sul lato Client e lato Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 589ca305ee7fe492dd5342ab184b37abcfb5d2ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064412"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Architettura della formattazione XML sul lato client e sul lato server (SQLXML 4.0)
  Nell'illustrazione seguente viene mostrata l'architettura della formattazione XML sul lato server.  
  
 ![Architettura della formattazione XML sul lato server. ] (../../../database-engine/dev-guide/media/serversidexml.gif "Formattazione sul lato server architettura di XML.")  
  
 In questo esempio il comando specificato sul client viene inviato al server. Il server produce un documento XML e lo restituisce al client. In questo caso, il server dispone di un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Grazie alla formattazione XML sul lato server, è possibile utilizzare il provider SQLXMLOLEDB o il provider SQLOLEDB.  Il provider SQLXMLOLEDB utilizza Sqlxml4.dll che è incluso in SQLXML 4.0. Quando si utilizza il provider SQLOLEDB, per impostazione predefinita si ottiene la funzionalità SQLXML fornita dal file Sqlxmlx.dll incluso in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows o in Microsoft Data Access Components (MDAC) 2.6 o versione successiva. Per utilizzare Sqlxml4.dll con SQLOLEDB, è necessario impostare la proprietà di SQLXML Version su "SQLXML.4.0" sull'oggetto connessione SQLOLEDB. In entrambi i casi, il server produce il documento XML e lo invia al client.  
  
> [!NOTE]  
>  Gli updategram e le query XPath vengono analizzati sul client. Per ottenere il modello XPath o la funzionalità degli updategram in SQLXML 4.0, utilizzare Sqlxml4.dll.  
  
 Nell'illustrazione seguente viene mostrata l'architettura della formattazione XML sul lato client.  
  
 ![Architettura della formattazione XML sul lato client. ] (../../../database-engine/dev-guide/media/clientsidexml.gif "Architettura del XML formattazione sul lato client.")  
  
 In questo esempio il client utilizza il provider SQLXMLOLEDB. Nella stringa di connessione, il Provider di dati deve essere impostata su SQLOLEDB. ovvero l'unico valore accettato in SQLXML 4.0. Il comando eseguito sul client viene inviato al server. Il set di righe generato nel server viene inviato al client. Sul client viene eseguita la formattazione del documento XML dal set di righe.  
  
 In SQLXML 4.0 è possibile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) o il provider SQLOLEDB come provider di dati. È possibile accedere a qualsiasi origine dati. La trasformazione XML può essere applicata al client purché la query restituisca un singolo set di righe.  
  
  
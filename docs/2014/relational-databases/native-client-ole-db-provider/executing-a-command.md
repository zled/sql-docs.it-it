---
title: Esegue un comando | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d9c0f935bf4d3cd903346281080a8b08384c1e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156684"
---
# <a name="executing-a-command"></a>Esecuzione di un comando
  Dopo aver stabilita la connessione a un'origine dati, il consumer chiama il **IDBCreateSession:: CreateSession** metodo per creare una sessione. La sessione funge da comando, set di righe o factory di transazioni.  
  
 Per utilizzare direttamente singoli indici o tabelle, il consumer richiede l'interfaccia `IOpenRowset`. Il metodo `IOpenRowset::OpenRowset` viene aperto e restituisce un set di righe che include tutte le righe di un singolo indice o tabella di base.  
  
 Per eseguire un comando (ad esempio SELECT \* FROM Authors), il consumer richiede il `IDBCreateCommand` interfaccia. Il consumer può eseguire il metodo `IDBCreateCommand::CreateCommand` per creare un oggetto comando e richiedere l'interfaccia `ICommandText`. Il metodo `ICommandText::SetCommandText` viene utilizzato per specificare il comando da eseguire.  
  
 Per eseguire il comando, viene utilizzato `Execute`. Il comando può essere qualsiasi nome di istruzione o di procedura SQL. Non tutti i comandi producono un oggetto set di risultati (set di righe). Comandi come SELECT * FROM Authors producono un set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del provider OLE DB di SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
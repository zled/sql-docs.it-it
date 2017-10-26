---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 49eb8e4472666be24a7edd1549dfe0e3705fd939
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|945|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DB_IS_SHUTDOWN|  
|Testo del messaggio|Impossibile aprire il database '%.*ls' a causa di file inaccessibili oppure per memoria o spazio su disco insufficiente.  Per ulteriori informazioni, vedere il log degli errori di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
Non è stato possibile accedere al database perché i file o altre risorse risultano mancanti.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare se nel log degli errori sono presenti ulteriori informazioni sull'errore relativo alla memoria, allo spazio su disco o alle autorizzazioni. Verificare il percorso dei file con estensione mdf e ndf del database interessato. Verificare inoltre che l'account utilizzato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] disponga dell'autorizzazione per accedere a tali file. Dopo aver corretto il problema, riavviare il database utilizzando ALTER DATABASE per impostarlo su ONLINE.  
  


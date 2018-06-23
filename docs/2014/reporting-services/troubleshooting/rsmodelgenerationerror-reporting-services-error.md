---
title: rsModelGenerationError - Errore di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 56d11e875a5b415aa890cedcf5466551cc51614f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155920"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsRenderingError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errore durante la generazione del modello. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Spiegazione  
 Il modello di report non è stato generato. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 e versioni precedenti questo errore viene visualizzato con maggior probabilità quando l'oggetto System.Data.DataSet non è in grado di gestire una tabella o una relazione all'interno dello schema del database, ad esempio quando vengono definite due chiavi esterne nella stessa colonna di una tabella.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per determinare il motivo specifico che ha causato la visualizzazione del messaggio, esaminare i file di log del server di report, nel percorso \Microsoft SQL Server\\<Istanza di SQL Server\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Solo interno  
  
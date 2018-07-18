---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 860fce7c9e8794fce89c76c7f6abb51a1a6773d2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421010"
---
# <a name="mssqlserver845"></a>MSSQLSERVER_845
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|845|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|BUFLATCH_TIMEOUT|  
|Testo del messaggio|Timeout durante l'attesa di un latch del buffer di tipo %d per la pagina %S_PGID, ID di database %d.|  
  
## <a name="explanation"></a>Spiegazione  
 Un processo in attesa di acquisire un latch non è stato in grado di acquisirne uno prima della scadenza del limite di tempo. Ciò può verificarsi se il completamento di un'operazione di I/O richiede una quantità di tempo eccessiva, in genere a causa di un blocco dei processi di sistema determinato da altre attività. In alcuni casi, tuttavia, può essere dovuto a un errore hardware.  
  
## <a name="user-action"></a>Azione dell'utente  
 È possibile impedire che si verifichi questo errore eseguendo le attività seguenti:  
  
-   Ridurre il carico di lavoro.  
  
-   Verificare se sono presenti errori di I/O associati nel log degli errori o nel log eventi. Gli errori di I/O sono in genere causati da un malfunzionamento del disco.  
  
-   Verificare nel log degli errori se sono presenti attività che non cedono il controllo e altri errori critici.  
  
-   Se si verificano spesso errori critici, ad esempio di asserzione, risolvere tali problemi.  
  
 Se l'errore persiste, contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
  

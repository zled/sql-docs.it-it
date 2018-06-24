---
title: MSSQLSERVER_823 | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a3889444fb2c605bccd36d30dbe324f220bbe942
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063117"
---
# <a name="mssqlserver823"></a>MSSQLSERVER_823
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|823|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|B_HARDERR|  
|Testo del messaggio|Il sistema operativo ha restituito l'errore %ls a SQL Server durante un'operazione %S_MSG, all'offset %#016I64x nel file '%ls'. Per informazioni più dettagliate, vedere i messaggi aggiuntivi nel log degli errori di SQL Server e nel registro eventi di sistema. Si tratta di una condizione di errore grave a livello di sistema, che può compromettere l'integrità del database e deve essere corretta immediatamente. Eseguire un controllo di consistenza completo del database (DBCC CHECKDB). L'errore può essere causato da molti fattori. Per ulteriori informazioni, vedere la documentazione online di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
 Una richiesta di lettura o scrittura di Windows non è stata eseguita. Il messaggio include il codice di errore restituito da Windows e il testo corrispondente. Nel caso di una richiesta di lettura, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono eseguiti quattro tentativi prima di generare il messaggio. Il problema è spesso dovuto a un errore hardware, ma può essere causato dal driver del dispositivo. Per altre informazioni sull'errore 823, vedere [http://support.microsoft.com/kb/828339](http://support.microsoft.com/kb/828339). Per altre informazioni sugli errori di I/O, vedere il capitolo 2 della pagina relativa alle [nozioni fondamentali sull'I/O in Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Azione dell'utente  
 Per ulteriori informazioni vedere il registro eventi di sistema. Contattare il produttore dell'hardware o il Servizio Supporto Tecnico Clienti Microsoft per determinare la causa e l'azione di correzione appropriata. Dopo la correzione dell'errore hardware, ripristinare tutti i database ed eseguire DBCC CHECKDB.  
  
  
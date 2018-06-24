---
title: Modifiche al comportamento in syslockinfo e sp_lock | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 982f31bbffb32726089fa331d105bfc262fc16a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065024"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>Modifiche al comportamento in syslockinfo e sp_lock
  **syslockinfo** e **sp_lock** possono restituire valori imprevisti. Possono inoltre restituire righe aggiuntive, mentre precedenti versioni di **syslockinfo** e **sp_lock** ha restituito un massimo di due righe per ogni risorsa di blocco.  
  
 Per accedere alle informazioni da **syslockinfo** o eseguire **sp_lock** è richiesta l'autorizzazione VIEW SERVER STATE nel server.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], il **rsc_objid** e **rsc_indid** colonne **syslockinfo** e il **objid** e **indid**  colonne **sp_lock** restituire l'ID di oggetto in modo coerente e l'ID indice In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è possibile che venga restituito il valore 0.  
  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** e **sp_lock** restituire un massimo di due righe per qualsiasi risorsa di blocco specificata in una singola transazione. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], quando il partizionamento dei blocchi è abilitato, è possibile che vengano restituite più righe per la stessa risorsa eseguita in una transazione. Si possono essere fino a N + 1 righe restituito, dove N è il numero di CPU. È inoltre possibile che vengano visualizzate richieste GRANTED e WAITING per la stessa risorsa, il che non è possibile in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

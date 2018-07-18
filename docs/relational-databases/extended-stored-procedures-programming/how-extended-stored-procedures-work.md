---
title: Funzionamento Stored procedure estese | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bd0996750aff15fc94a17b669092552a021bf34b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="how-extended-stored-procedures-work"></a>Funzionamento delle stored procedure estese
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Il funzionamento di una stored procedure estesa è il seguente:  
  
1.  Quando un client esegue una stored procedure estesa, la richiesta viene trasmessa in flusso di dati tabulare (TDS) o formato SOAP Simple Object Access Protocol () dall'applicazione client per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue la ricerca della DLL associata alla stored procedure estesa e, se non è già caricata, la carica.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chiama la stored procedure estesa richiesta (implementata come funzione all'interno della DLL).  
  
4.  La stored procedure estesa passa set di risultati e restituisce parametri al server mediante l'API Stored procedure estesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di stored procedure estese del motore di database](../../relational-databases/database-engine-extended-stored-procedure-programming.md)  
  
  

---
title: Funzionamento Stored procedure estese | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7ceb2fd3c9069d762d5e0a317a256fcd92dbe186
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184741"
---
# <a name="how-extended-stored-procedures-work"></a>Funzionamento delle stored procedure estese
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Il funzionamento di una stored procedure estesa è il seguente:  
  
1.  Quando un client esegue una stored procedure estesa, la richiesta viene trasmessa in flusso di dati tabulare (TDS) o formato SOAP Simple Object Access Protocol () dall'applicazione client per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue la ricerca della DLL associata alla stored procedure estesa e, se non è già caricata, la carica.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chiama la stored procedure estesa richiesta (implementata come funzione all'interno della DLL).  
  
4.  La stored procedure estesa passa set di risultati e restituisce parametri al server mediante l'API Stored procedure estesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di stored procedure estese del motore di database](../database-engine-extended-stored-procedure-programming.md)  
  
  

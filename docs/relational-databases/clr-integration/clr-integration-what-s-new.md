---
title: Novità&#39;s New in integrazione con CLR | Documenti Microsoft
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ab0a803920a06a3e4924261626f76485ba3d6381
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="clr-integration---what39s-new"></a>Integrazione con CLR, quali&#39;s New
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Di seguito sono elencate le nuove caratteristiche dell'integrazione con CLR in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   Nella versione 4 di CLR tramite gli oggetti di database CLR non vengono più rilevate le eccezioni relative allo stato danneggiato. Queste eccezioni vengono ora rilevate nel livello host dell'integrazione con CLR. Queste eccezioni possono ancora essere rilevate dai componenti di database CLR impostando un attributo di codice ([\<legacyCorruptedStateExceptionsPolicy > elemento](http://go.microsoft.com/fwlink/?LinkId=204954)). Questa operazione non è tuttavia consigliata, in quanto i risultati non sono affidabili nel caso di un'eccezione relativa allo stato danneggiato.  
  
-   A causa dei rigidi requisiti di sicurezza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], nei componenti di database CLR continua a essere utilizzato il modello di sicurezza dall'accesso di codice definito nella versione 2.0 di CLR.  
  
-   In CLR versione 4, un errore di formato in un **System. TimeSpan** valore genererà un **System.FormatExceptions**. Prima della versione 4 di CLR, un errore di formato in un **System. TimeSpan** viene ignorato. Applicazioni di database che si basano sul comportamento precedenti alla versione 4 di CLR deve essere eseguito con un livello di compatibilità del database (**del livello di compatibilità di ALTER DATABASE**) pari a 100 o inferiore. Per ulteriori informazioni, vedere [< TimeSpan_LegacyFormatMode > elemento](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   La versione 4 di CLR supporta Unicode 5.1. Le operazioni di ordinamento che includono accenti e simboli verranno migliorate. Possono verificarsi problemi di compatibilità se l'applicazione è basata sul comportamento di ordinamento delle versioni precedenti. Per abilitare l'ordinamento, il livello di compatibilità del database legacy (**del livello di compatibilità di ALTER DATABASE**) deve essere impostato su 100 o inferiore. Per offrire il supporto necessario, tramite [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] viene installato il file sort00001000.dll nella directory di .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Per ulteriori informazioni, vedere [ \<CompatSortNLSVersion > elemento](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Le colonne seguenti sono stati aggiunti [Sys.dm clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**, e **survived_ memory_kb**.  
  
  

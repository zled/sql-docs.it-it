---
title: Cosa&#39;s di integrazione con CLR | Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 55cb6537db540fb5d916b72cb1b469dc3846f419
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356213"
---
# <a name="clr-integration---what39s-new"></a>Integrazione CLR - Novità&#39;New s
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Di seguito sono elencate le nuove caratteristiche dell'integrazione con CLR in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]:  
  
-   Nella versione 4 di CLR tramite gli oggetti di database CLR non vengono più rilevate le eccezioni relative allo stato danneggiato. Queste eccezioni vengono ora rilevate nel livello host dell'integrazione con CLR. Queste eccezioni possono ancora essere rilevate da componenti di database CLR impostando un attributo di codice ([\<legacyCorruptedStateExceptionsPolicy > elemento](http://go.microsoft.com/fwlink/?LinkId=204954)). Questa operazione non è tuttavia consigliata, in quanto i risultati non sono affidabili nel caso di un'eccezione relativa allo stato danneggiato.  
  
-   A causa dei rigidi requisiti di sicurezza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], nei componenti di database CLR continua a essere utilizzato il modello di sicurezza dall'accesso di codice definito nella versione 2.0 di CLR.  
  
-   Nella versione 4 di CLR un errore di formato in una **System. TimeSpan** valore genererà una **System.FormatExceptions**. Prima della versione 4 di CLR, un errore di formato in una **System. TimeSpan** viene ignorato. Applicazioni di database che si basano sul comportamento prima della versione 4 di CLR deve essere eseguita con un livello di compatibilità del database (**livello di compatibilità ALTER DATABASE**) pari a 100 o inferiore. Per altre informazioni, vedere [< TimeSpan_LegacyFormatMode > elemento](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   La versione 4 di CLR supporta Unicode 5.1. Le operazioni di ordinamento che includono accenti e simboli verranno migliorate. Possono verificarsi problemi di compatibilità se l'applicazione è basata sul comportamento di ordinamento delle versioni precedenti. Per abilitare l'ordinamento, il livello di compatibilità del database legacy (**livello di compatibilità ALTER DATABASE**) deve essere impostato su 100 o inferiore. Per offrire il supporto necessario, tramite [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] viene installato il file sort00001000.dll nella directory di .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Per altre informazioni, vedere [ \<CompatSortNLSVersion > elemento](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Le colonne seguenti sono stati aggiunti al [DM clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**, e **survived_ memory_kb**.  
  
  

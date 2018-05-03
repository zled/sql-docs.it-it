---
title: Schema di versione driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dafb9631a3031c60646e4a7c396fadc440e12bb3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="driver-version-scheme"></a>Schema di versione driver
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Nella tabella seguente sono elencate tutte le versioni rilasciate di Microsoft ODBC Driver for Oracle.  
  
|Versione del driver|Numero di build|Cronologia disponibilità|  
|--------------------|------------------|--------------------------|  
|1,0|2.00.6235|Visual C++ 4.2 e Visual Basic 5.0, Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 e MDAC 1,5 a|  
|2.0 aggiornato|2.73.7283.01|IIS 4.0|  
|2.0 aggiornato|2.73.7283.03|MDAC 1.5b e 1.5 c|  
|2.0 aggiornato|2.73.7356|SDK DI ODBC 3.5|  
|2.5|2.573.2927|Visual Studio 6.0 e MDAC 2.0|  
|2.5 aggiornato|2.573.3513|SQL Server 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 Compilazione 2.00.6235 (versione 1) è la prima versione del Driver ODBC di Microsoft per Oracle. Dopo il rilascio della prima versione, è stata adottata una convenzione di denominazione di nuovo.  
  
 Ad esempio, 2.73.7283.03 può essere suddiviso nei seguenti componenti distinti:  
  
-   2 = il numero di versione.  
  
-   73 = la versione del Server Oracle per il quale è stato progettato il driver.  
  
-   7283.03 = il numero di build del driver.  
  
> [!NOTE]  
>  Con la versione 2.573.2973, la convenzione di denominazione ha portato a qualche confusione che 2.573 è una versione precedente di 2,73, ma ogni sezione del numero di compilazione deve essere considerato singolarmente. Il numero 573 è maggiore di 73, pertanto è una versione più recente. Inoltre, "2.5" indica il numero di versione del driver.

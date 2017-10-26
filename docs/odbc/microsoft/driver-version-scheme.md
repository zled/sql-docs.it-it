---
title: Schema di versione driver | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e3a8132d535b764818fb9dcab72b3cba8bb48154
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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


---
title: Impostazione DCOM flusso marshalling formato | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c63b304e6ee2c2060be1b0233e10197adc955427
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274440"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Impostazione DCOM flusso formato di marshalling
Un computer client mediante i componenti di RDS 1.5 o versioni precedenti non è compatibile con un server mediante i componenti da RDS 2.0 o versione successiva. Quando si utilizza DCOM come protocollo sottostante, il supporto per RDS 2.0 o versione successiva è più efficiente nel trasporto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti. Se il client è in esecuzione i componenti di servizi desktop remoto 1.5 o versioni precedenti, è possibile impostare il server da utilizzare con il supporto di servizi desktop remoto precedente (denominata RDS 1.0) o il supporto di servizi desktop remoto più recente (denominata RDS 2.0 o versione successiva). Impostare una delle voci del Registro di sistema seguenti:  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 oppure  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```



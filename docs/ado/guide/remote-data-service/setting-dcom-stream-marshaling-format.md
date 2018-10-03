---
title: Impostare Stream DCOM formato di marshalling | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33359afb2910c75e34ff38c9606ff71b3760cbc1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802859"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Configurazione del formato di marshalling del flusso DCOM
Un computer client mediante i componenti di servizi desktop remoto 1.5 o versioni precedenti non è compatibile con un server mediante i componenti dalla versione 2.0 di servizi desktop remoto o in un secondo momento. Quando si usa DCOM come protocollo sottostante, il supporto per Servizi Desktop remoto 2.0 o versione successiva è più efficiente nel trasporto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti. Se il client è in esecuzione i componenti di servizi desktop remoto 1.5 o versioni precedenti, è possibile impostare il server per lavorare con il precedente supporto di servizi desktop remoto (denominato Servizi Desktop remoto 1.0) o il supporto di servizi desktop remoto più recente (denominato Servizi Desktop remoto 2.0 o versione successiva). Impostare una delle voci del Registro di sistema seguenti:  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 oppure  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```



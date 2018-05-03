---
title: Proprietà Recordset e SourceRecordset (RDS) | Documenti Microsoft
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e934983f54be5644e945e4ecdcf201b793c33ea4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Proprietà Recordset e SourceRecordset (RDS)
Indica il **Recordset** oggetto restituito da un oggetto di business personalizzata.  
  
 **Si applica a:** [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *Recordset*  
 Una variabile oggetto che rappresenta un **Recordset** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile impostare il **SourceRecordset** proprietà per un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) restituito da un oggetto di business personalizzata.  
  
 Queste proprietà consentono a un'applicazione per gestire il processo di associazione tramite un processo personalizzato. Ricevono un set di righe inserito in un **Recordset** in modo che sia possibile interagire direttamente con il **Recordset**, eseguire azioni quali l'impostazione delle proprietà o l'iterazione di **Recordset** .  
  
 È possibile impostare il **SourceRecordset** proprietà o a leggere la **Recordset** proprietà in fase di esecuzione nel codice di script.  
  
 **SourceRecordset** è una proprietà di sola scrittura, in contrasto con il **Recordset** proprietà, che è una proprietà di sola lettura.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà di SourceRecordset (VBScript) e Recordset](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Metodo CreateRecordset (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Metodo Query (Servizi Desktop remoto)](../../../ado/reference/rds-api/query-method-rds.md)



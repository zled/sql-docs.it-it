---
title: Codici di errore DataControl | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0886839245fa7a4dc0e2baee0dfaf010ff876e70
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="datacontrol-object-error-codes"></a>Codici di errore dell'oggetto DataControl
La tabella seguente elenca i [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) codici di errore dell'oggetto. Conversione decimale positiva dei due byte bassi, vengono visualizzati la conversione decimale negativa del codice di errore completo e i valori esadecimali.

|RDS. Codici di errore DataControl|Number|Description|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107-2146824175 0x800A1011|Impossibile eseguire l'operazione mentre è in sospeso un'operazione asincrona.|
|**IDS_BadInlineTablegram**|4105-2146824183 0x800A1009|Viene inline non valido.|
|**IDS_CantConnect**|4099-2146824189 0x800A1003|Impossibile connettersi al server.|
|**IDS_CantCreateObject**|4100-2146824188 0x800A1004|Impossibile creare l'oggetto business.|
|**IDS_CantFindDataspace**|4102-2146824186 0x800A1006|Proprietà DataSpace non è valido.|
|**IDS_CantInvokeMethod**|4101-2146824187 0x800A1005|Impossibile richiamare il metodo sull'oggetto business.|
|**IDS_CrossDomainWarning**|4112-2146824170 0x800A1016|Questa pagina accede ai dati in un altro dominio. Si desidera consentire questa operazione? Per evitare questo messaggio in Internet Explorer, è possibile aggiungere un sito Web protetto all'area siti attendibili nel **sicurezza** scheda della finestra di **Opzioni Internet** la finestra di dialogo.|
|**IDS_InvalidADCClientVersion**|4106-2146824176 0x800A1010|Versione Client di servizi desktop remoto non valido: Client è più recente di server.|
|**IDS_INVALIDARG**|5376-2147019520 0x80071500|Uno o più argomenti non sono validi.|
|**IDS_InvalidBindings**|4097-2146824191 0x800A1001|Errore nella proprietà di binding.|
|**IDS_InvalidParam**|4110-2146824172 0x800A1014|Uno o più argomenti non sono validi.|
|**IDS_NOINTERFACE**|5377-2147019519 0x80071501|Interfaccia non è supportata.|
|**IDS_NotReentrant**|4111-2146824171 0x800A1015|Richiesta non può essere eseguita durante l'elaborazione del gestore dell'evento.|
|**IDS_ObjectNotSafe**|4103-2146824185 0x800A1007|Le impostazioni di sicurezza nel computer impediscono la creazione dell'oggetto business.|
|**IDS_RecordsetNotOpen**|4109-2146824173 0x800A1013|**Recordset** non è aperta.|
|**IDS_ResetInvalidField**|4108-2146824174 0x800A1012|La colonna specificata in **SortColumn** o **FilterColumn** non esiste.|
|**IDS_RowsetNotUpdateable**|4104-2146824184 0x800A1008|Set di righe non aggiornabile.|
|**IDS_UnexpectedError**|4351-2146823937 0x800A10FF|Errore imprevisto.|
|**IDS_UpdatesFailed**|4098-2146824190 0x800A1002|Impossibile aggiornare il database.|
|**IDS_URLMONNotFound**|4119-2146824169 0x800A1017|DataControl **URL** proprietà richiede il file di sistema Urlmon.dll, che non è stato trovato.|

## <a name="see-also"></a>Vedere anche
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)

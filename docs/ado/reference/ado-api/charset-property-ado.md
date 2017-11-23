---
title: "Proprietà set di caratteri (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Stream::Charset
helpviewer_keywords: Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ded981a9ed4905aa607d8b19fe010682b61b5780
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="charset-property-ado"></a>Proprietà set di caratteri (ADO)
Indica il set di caratteri in cui il contenuto di un testo [flusso](../../../ado/reference/ado-api/stream-object-ado.md) devono essere convertite per la memorizzazione nel buffer interno del **flusso** oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che specifica il carattere è impostato in cui il contenuto del **flusso** saranno convertiti. Il valore predefinito è **Unicode**. I valori consentiti sono stringhe tipiche passate attraverso l'interfaccia come nomi di set di caratteri di Internet (ad esempio, "iso-8859-1", "Windows-1252" e così via). Per un elenco di set di nomi di caratteri che sono noti a un sistema, vedere il sottochiavi HKEY_CLASSES_ROOT\MIME\Database\Charset del Registro di sistema.  
  
## <a name="remarks"></a>Osservazioni  
 In un testo **flusso** dell'oggetto, dati di testo vengono archiviati nel set di caratteri specificato da di **Charset** proprietà. Il valore predefinito è Unicode. Il **Charset** proprietà viene utilizzata per la conversione dei dati verso il **flusso** o prossimi fuori il **flusso**. Ad esempio, se il **flusso** contiene dati ISO-8859-1 e che i dati vengono copiati in BSTR, il **flusso** oggetto convertirà i dati in formato Unicode. È anche vero il contrario.  
  
 Per un oggetto aperto **flusso**, corrente [posizione](../../../ado/reference/ado-api/position-property-ado.md) deve essere all'inizio del **flusso** (0) per essere in grado di impostare **Charset**.  
  
 **Set di caratteri** viene utilizzato solo con testo **flusso** oggetti ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Questa proprietà viene ignorata se **tipo** è **adTypeBinary**.  
  
 Per un esempio di codice, vedere [passaggio 4: popolare la casella di testo Details](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

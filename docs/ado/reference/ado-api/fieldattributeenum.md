---
title: FieldAttributeEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dfac02887d8f66066a11674ca6dded410df709aa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Specifica uno o più attributi di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Indica che il provider memorizza nella cache i valori dei campi e che le letture successive vengono eseguite dalla cache.|  
|**adFldFixed**|0x10|Indica che il campo dati a lunghezza fissa.|  
|**adFldIsChapter**|0x2000|Indica che il campo contiene un valore di capitolo, che specifica un recordset figlio specifico correlato al campo padre. Campi dei capitoli vengono generalmente utilizzati con il data shaping o filtri.|  
|**adFldIsCollection**|0x40000|Indica che il campo specifica che la risorsa rappresentata dal record è una raccolta di altre risorse, ad esempio una cartella, anziché a una risorsa semplice, ad esempio un file di testo.|  
|**adFldKeyColumn**|0x8000|Indica che il campo specificato in tutto o parte di chiave primaria della colonna.|  
|**adFldIsDefaultStream**|0x20000|Indica che il campo contiene il flusso predefinito per la risorsa rappresentata dal record. Ad esempio, il flusso predefinito può essere contenuto HTML di una cartella radice in un sito Web, che viene pubblicato automaticamente quando viene specificato l'URL radice.|  
|**adFldIsNullable**|0x20|Indica che il campo ammette valori null.|  
|**adFldIsRowURL**|0x10000|Indica che il campo contiene l'URL che corrisponde al nome della risorsa dall'archivio dati rappresentato dall'oggetto record.|  
|**adFldLong**|0x80|Indica che il campo è un campo binario lungo. Indica inoltre che è possibile utilizzare il [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) e [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) metodi.|  
|**adFldMayBeNull**|0x40|Indica che è possibile leggere i valori null dal campo.|  
|**adFldMayDefer**|0x2|Indica che il campo viene posticipato, vale a dire i valori dei campi non vengono recuperati dall'origine dati con il record completo, ma solo quando si accede in modo esplicito.|  
|**adFldNegativeScale**|0x4000|Indica che il campo rappresenta un valore numerico da una colonna che supporta valori di scala negativa. La scala viene specificata per il [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) proprietà.|  
|**adFldRowID**|0x100|Indica che il campo contiene un identificatore di riga persistente che non può essere scritta senza alcun valore significativo, ad eccezione per identificare la riga (ad esempio un numero di record, l'identificatore univoco e così via).|  
|**adFldRowVersion**|0x200|Indica che il campo contiene un tipo di indicatore di data e ora utilizzato per tenere traccia degli aggiornamenti.|  
|**adFldUnknownUpdatable**|0x8|Indica che il provider non è possibile determinare se è possibile scrivere nel campo.|  
|**adFldUnspecified**|-0xFFFFFFFF 1|Indica che il provider non siano specificati gli attributi di campo.|  
|**adFldUpdatable**|0x4|Indica che è possibile scrivere nel campo.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.FieldAttribute.CACHEDEFERRED|  
|AdoEnums.FieldAttribute.FIXED|  
|AdoEnums.FieldAttribute.ISNULLABLE|  
|AdoEnums.FieldAttribute.LONG|  
|AdoEnums.FieldAttribute.MAYBENULL|  
|AdoEnums.FieldAttribute.MAYDEFER|  
|AdoEnums.FieldAttribute.NEGATIVESCALE|  
|AdoEnums.FieldAttribute.ROWID|  
|AdoEnums.FieldAttribute.ROWVERSION|  
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE|  
|AdoEnums.FieldAttribute.UNSPECIFIED|  
|AdoEnums.FieldAttribute.UPDATABLE|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Append (metodo) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|

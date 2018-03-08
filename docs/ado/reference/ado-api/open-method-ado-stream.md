---
title: Open (metodo) (flusso ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b104e04c81fce3fce5cb25d175602f1b339e9ac1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="open-method-ado-stream"></a>Open (metodo) (flusso ADO)
Apre un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto per gestire i flussi di dati binario o di testo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **Variant** valore che specifica l'origine dei dati per il **flusso**. *Origine* può contenere una stringa URL assoluto che punta a un nodo esistente in una struttura ben noti, ad esempio un sistema di posta elettronica o file. È necessario specificare un URL utilizzando la parola chiave URL ("URL =*schema*://*server*/*cartella*"). In alternativa, *origine* può contenere un riferimento a un già aperto [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto, che consente di aprire il flusso predefinito associato con il **Record**. Se *origine* non è stato specificato un **flusso** creata e aperta, associata a Nessuna origine sottostante per impostazione predefinita. Per ulteriori informazioni sugli schemi URL e i provider associati, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Mode*  
 Facoltativa. Oggetto [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) valore che specifica la modalità di accesso per i risultanti **flusso** (ad esempio, di lettura/scrittura o sola lettura). Valore predefinito è **adModeUnknown**. Vedere il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà per ulteriori informazioni sulle modalità di accesso. Se *modalità* viene omesso, viene ereditato dall'oggetto di origine. Ad esempio, se l'origine **Record** viene aperto in modalità di sola lettura, la **flusso** verrà inoltre aperta in modalità di sola lettura per impostazione predefinita.  
  
 *OpenOptions*  
 Facoltativa. Oggetto [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) valore. Valore predefinito è **adOpenStreamUnspecified**.  
  
 *UserName*  
 Facoltativa. Oggetto **stringa** valore che contiene l'ID utente che, se necessario, accede il **flusso** oggetto.  
  
 *Password*  
 Facoltativa. Oggetto **stringa** valore contenente la password che, se necessario, accede il **flusso** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Quando un **Record** oggetto viene passato come parametro di origine, il *UserID* e *Password* parametri non vengono utilizzati perché l'accesso al **Record** oggetto è già disponibile. Analogamente, il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) del **Record** oggetto viene trasferito al **flusso** oggetto. Quando *origine* non viene specificato, il **flusso** aperto non contiene dati ed è un [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) pari a zero (0). Per evitare la perdita di dati scritto in questo **flusso** quando il **flusso** è chiuso, salvare il **flusso** con il [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) o [ SaveToFile](../../../ado/reference/ado-api/savetofile-method.md) metodi, o salvarlo in un'altra posizione di memoria.  
  
 Un *OpenOptions* valore **adOpenStreamFromRecord** identifica il contenuto di *origine* parametro sia un già aperto **Record**oggetto. Il comportamento predefinito consiste nel considerare *origine* come un URL che punta direttamente a un nodo in una struttura ad albero, ad esempio un file. Viene aperto il flusso predefinito associato a tale nodo.  
  
 Mentre il **flusso** è non è aperta, è possibile leggere tutte le proprietà di sola lettura del **flusso**. Se un **flusso** viene aperto in modo asincrono, tutte le operazioni successive (diverso da controllo il [stato](../../../ado/reference/ado-api/state-property-ado.md) e altre proprietà di sola lettura) vengono bloccate finché il **aprire** operazione completata.  
  
 Oltre alle opzioni descritti in precedenza, specificando non *origine*, è possibile creare un'istanza di un **flusso** oggetto in memoria senza associarla a un'origine sottostante. È possibile aggiungere dati in modo dinamico nel flusso da scrivere i dati di testo o binari il **flusso** con [scrivere](../../../ado/reference/ado-api/write-method.md) o [WriteText](../../../ado/reference/ado-api/writetext-method.md), o il caricamento dei dati da un file con [ LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Metodo OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Metodo SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)

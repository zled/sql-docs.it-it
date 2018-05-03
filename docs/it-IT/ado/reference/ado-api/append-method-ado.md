---
title: Append (metodo) (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff92549b842fbc180d63e52e9576b857c476ecd3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-ado"></a>Append (metodo) (ADO)
Aggiunge un oggetto a una raccolta. Se la raccolta è [campi](../../../ado/reference/ado-api/fields-collection-ado.md), un nuovo [campo](../../../ado/reference/ado-api/field-object.md) oggetto può essere creato prima di essere aggiunto alla raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Parametri  
 *raccolta*  
 Oggetto raccolta.  
  
 *Campi*  
 Oggetto **campi** insieme.  
  
 *oggetto*  
 Una variabile oggetto che rappresenta l'oggetto da aggiungere.  
  
 *Nome*  
 Oggetto **stringa** valore contenente il nome del nuovo **campo** dell'oggetto e non deve essere lo stesso nome come qualsiasi altro oggetto nel *campi*.  
  
 *Tipo*  
 Oggetto [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valore, il cui valore predefinito è **adEmpty**, che specifica il tipo di dati del nuovo campo. I seguenti tipi di dati non supportati da ADO e dovrebbe non essere utilizzato quando aggiungendo nuovi campi a un [Recordset ADO (Object)](../../../ado/reference/ado-api/recordset-object-ado.md): **adIDispatch**, **adIUnknown**, **adVariant**.  
  
 *DefinedSize*  
 Facoltativa. Oggetto **lungo** valore che rappresenta le dimensioni definite, in caratteri o byte, del nuovo campo. Il valore predefinito per questo parametro è derivato da *tipo*. Campi che dispongono di un *DefinedSize* maggiori di 255 byte vengono considerati come colonne di lunghezza variabile. Il valore predefinito per *DefinedSize* non è specificato.  
  
 *Attrib*  
 Facoltativa. Oggetto [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) valore, il cui valore predefinito è **adFldDefault**, che specifica gli attributi per il nuovo campo. Se questo valore viene omesso, il campo conterrà gli attributi derivati da *tipo*.  
  
 *Valore FieldValue*  
 Facoltativa. Oggetto **Variant** che rappresenta il valore per il nuovo campo. Se non specificato, il campo viene aggiunto con un valore null.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="parameters-collection"></a>Raccolta Parameters  
 È necessario impostare il [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà di un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto prima dell'aggiunta per il [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme. Se si seleziona un tipo di dati a lunghezza variabile, è necessario impostare anche la [dimensioni](../../../ado/reference/ado-api/size-property-ado-parameter.md) su un valore maggiore di zero.  
  
 Che descrive i parametri manualmente riduce al minimo le chiamate al provider e pertanto consente di migliorare le prestazioni quando si utilizzano stored procedure o query con parametri. Tuttavia, è necessario conoscere le proprietà dei parametri associati la stored procedure o parametri di query che si desidera chiamare.  
  
 Utilizzare il [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) metodo per creare **parametro** oggetti con le impostazioni di proprietà appropriato e l'utilizzo di **Append** metodo per aggiungerli al [ I parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme. Consente di impostare e restituire i valori dei parametri senza la necessità di chiamare il provider per le informazioni sui parametri. Se si sta scrivendo su un provider che non fornisce informazioni sui parametri, è necessario utilizzare questo metodo per compilare manualmente la **parametri** insieme per utilizzare i parametri.  
  
## <a name="fields-collection"></a>Raccolta Fields  
 Il *FieldValue* parametro è valido solo quando si aggiunge un **campo** l'oggetto in un [Record](../../../ado/reference/ado-api/record-object-ado.md) dell'oggetto, non a un **Recordset** oggetto. Con un **Record** dell'oggetto, è possibile aggiungere campi e specificare i valori nello stesso momento. Con un **Recordset** dell'oggetto, è necessario creare campi durante la **Recordset** è chiuso e quindi aprire il **Recordset** e assegnare valori ai campi.  
  
> [!NOTE]
>  Per i nuovi **campo** gli oggetti che sono stati accodati per il **campi** raccolta di un **Record** oggetto, il [valore](../../../ado/reference/ado-api/value-property-ado.md) deve essere impostata prima di qualsiasi altro **campo** le proprietà possono essere specificate. Innanzitutto, un valore specifico per il **valore** proprietà necessario è stata assegnata e [aggiornamento](../../../ado/reference/ado-api/update-method.md) sul **campi** raccolta denominata. Quindi, altre proprietà, ad esempio [tipo](../../../ado/reference/ado-api/type-property-ado.md) o [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) accessibili. **Campo** oggetti dei seguenti tipi di dati (**DataTypeEnum**) non possono essere accodati per il **campi** raccolta e causerà un errore: **adArray**, **adChapter**, **adEmpty**, **adPropVariant**, e **adUserDefined**. Inoltre, i tipi di dati seguenti non sono supportati da ADO: **adIDispatch**, **adIUnknown**, e **adIVariant**. Per questi tipi, si verificherà alcun errore quando aggiunto, ma utilizzo può produrre risultati imprevisti, tra cui le perdite di memoria.  
  
## <a name="recordset"></a>recordset  
 Se non si imposta la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà prima di chiamare il **Append** metodo **CursorLocation** verrà impostato su **adUseClient** ( un [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valore) automaticamente quando il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene chiamato l'oggetto.  
  
 Se si verificherà un errore di run-time di **Append** metodo viene chiamato sul **campi** insieme di open **Recordset**, o scegliere un **Recordset** in cui il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà è stata impostata. È possibile aggiungere solo i campi in un **Recordset** che non sia aperto e non è ancora stato connesso a un'origine dati. Si tratta in genere quando un **Recordset** oggetto viene creato con il [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) metodo o assegnata a una variabile oggetto.  
  
## <a name="record"></a>Record  
 Errore di run-time non si verificherà se il **Append** metodo viene chiamato sul **campi** insieme di open **Record**. Verrà aggiunto il nuovo campo per il **campi** insieme il **Record** oggetto. Se il **Record** è stata derivata da una **Recordset**, il nuovo campo non compariranno nella **campi** insieme del **Recordset** oggetto.  
  
 Un campo esistente non può essere creato e aggiunto al **campi** raccolta assegnando un valore per l'oggetto campo, come se esistesse già nella raccolta. L'assegnazione verrà attivata la creazione automatica e l'aggiunta del **campo** oggetto e l'assegnazione verrà completata.  
  
 Dopo l'aggiunta una **campo** per il **campi** raccolta di un **Record** dell'oggetto, chiamare il **aggiornamento** metodo il **campi**  insieme per salvare le modifiche.  
  
## <a name="applies-to"></a>Si applica a  
  
- [Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere e un esempio di metodi CreateParameter (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Aggiungere e CreateParameter metodi (VC + +)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Metodo Delete (insieme Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Metodo Delete (insieme Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete (metodo) (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Metodo Update](../../../ado/reference/ado-api/update-method.md)

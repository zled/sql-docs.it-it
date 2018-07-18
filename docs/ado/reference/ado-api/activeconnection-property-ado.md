---
title: Proprietà ActiveConnection (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6988f743abe5a6a0bf875da0b7e52bed23f7500
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275160"
---
# <a name="activeconnection-property-ado"></a>Proprietà ActiveConnection (ADO)
Indica a cui [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto specificato [comando](../../../ado/reference/ado-api/command-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), o [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto attualmente appartiene.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che contiene una definizione per una connessione se la connessione viene chiusa, o un **Variant** contenente corrente **connessione** oggetto se la connessione è aperta. Valore predefinito è un riferimento di oggetto null. Vedere il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **ActiveConnection** proprietà per determinare il **connessione** oggetto su cui specificato **comando** verrà eseguito l'oggetto o specificato  **Recordset** verrà aperto.  
  
## <a name="command"></a>Comando  
 Per **comando** oggetti, il **ActiveConnection** proprietà è di lettura/scrittura.  
  
 Se si tenta di chiamare il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo su un **comando** oggetto prima di impostare questa proprietà su un oggetto aperto **connessione** oggetto o stringa di connessione valida, si verifica un errore.  
  
 Se un **connessione** oggetto è assegnato il **ActiveConnection** proprietà, l'oggetto deve essere aperto. L'assegnazione di un oggetto connessione chiuso causa un errore.  
  
### <a name="note"></a>Nota  
 **Microsoft Visual Basic** impostazione il **ActiveConnection** proprietà *Nothing* rimuove l'associazione e il **comando** oggetto dall'oggetto corrente **Connessione** e fa sì che il provider di rilasciare le risorse associate nell'origine dati. È quindi possibile associare il **comando** oggetto con lo stesso o in un altro **connessione** oggetto. Alcuni provider consentono di modificare l'impostazione della proprietà da uno **connessione** a un altro, senza dover prima di impostare la proprietà su *nulla*.  
  
 Se il [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme il **comando** oggetto contiene i parametri forniti dal provider, la raccolta viene cancellata se si imposta la **ActiveConnection** proprietà *nulla* o a un altro **connessione** oggetto. Se si creano manualmente [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetti e usarli per riempire il **parametri** insieme del **comando** oggetto impostando il **ActiveConnection**  proprietà *nulla* o a un altro **connessione** oggetto lascia il **parametri** raccolta intatto.  
  
 Chiusura di **connessione** oggetto con cui un **comando** oggetto è set associati il **ActiveConnection** proprietà *nulla*. Impostando questa proprietà su un oggetto chiuso **connessione** oggetto genera un errore.  
  
## <a name="recordset"></a>recordset  
 Per aprire **Recordset** oggetti o per **Recordset** oggetti la cui proprietà [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) proprietà è impostata su un valore valido **comando** oggetto, il **ActiveConnection** proprietà è di sola lettura. In caso contrario, è di lettura/scrittura.  
  
 È possibile impostare questa proprietà su un valore valido **connessione** oggetto o a una stringa di connessione valida. In questo caso, il provider crea un nuovo **connessione** utilizzando questa definizione dell'oggetto e viene aperta la connessione. Inoltre, il provider può impostare questa proprietà per il nuovo **connessione** oggetto per fornire un modo per accedere il **connessione** per informazioni dettagliate sull'errore o per eseguire altri comandi dell'oggetto.  
  
 Se si utilizza il *ActiveConnection* argomento del [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) per aprire un **Recordset** oggetto, il **ActiveConnection** proprietà ereditare il valore dell'argomento.  
  
 Se si imposta la **origine** proprietà del **Recordset** oggetto su un valore valido **comando** variabile oggetto, il **ActiveConnection** proprietà di il **Recordset** eredita l'impostazione del **comando** dell'oggetto **ActiveConnection** proprietà.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando viene utilizzata su un lato client **Recordset** dell'oggetto, questa proprietà può essere impostata solo su una stringa di connessione o (in Microsoft Visual Basic o Visual Basic, Scripting Edition) a *Nothing* .  
  
## <a name="record"></a>Record  
 Questa proprietà è di lettura/scrittura quando il **Record** oggetto viene chiuso e può contenere una stringa di connessione o un riferimento a un oggetto aperto **connessione** oggetto. Questa proprietà è di sola lettura quando il **Record** oggetto è aperto e contiene un riferimento a un oggetto aperto **connessione** oggetto.  
  
 Oggetto **connessione** oggetto viene creato in modo implicito quando il **Record** oggetto viene aperto da un URL. Aprire il **Record** con un oggetto esistente, aprire **connessione** oggetto assegnando il **connessione** a questa proprietà dell'oggetto o tramite il **connessione** oggetto come parametro nel [aprire](../../../ado/reference/ado-api/open-method-ado-record.md) chiamata al metodo. Se il **Record** viene aperto da un oggetto esistente **Record** o [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), quindi è automaticamente associato a tale **Record** o  **Recordset** dell'oggetto **connessione** oggetto.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà direzione (VB), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Esempio di proprietà direzione (VC + +), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione proprietà esempio (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)

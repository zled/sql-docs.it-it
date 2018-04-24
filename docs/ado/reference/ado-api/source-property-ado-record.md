---
title: Proprietà (Record ADO) dell'origine | Documenti Microsoft
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
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 76c09225e13e0a17e7b1c3d9e4ba42b5128f6769
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="source-property-ado-record"></a>Proprietà Source (Record ADO)
Indica l'origine dati o l'oggetto rappresentato dal [Record](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Variant** valore che indica l'entità rappresentata dal **Record**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **origine** proprietà restituisce il *origine* argomento del **Record** oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-record.md) metodo. Può contenere una stringa URL assoluta o relativa. È possibile usare un URL assoluto senza impostare il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà per aprire direttamente il **Record** oggetto. Implicita **connessione** viene creato in questo caso l'oggetto.  
  
 Il **origine** proprietà può inoltre contenere un riferimento a un già aperto **Recordset**, che consente di aprire un **Record** oggetto che rappresenta la riga corrente nella  **Recordset**.  
  
 Il **origine** proprietà può contenere anche un riferimento a un [comando](../../../ado/reference/ado-api/command-object-ado.md) che restituisce una singola riga di dati dal provider.  
  
 Se il **ActiveConnection** anche è impostata, il **origine** proprietà deve puntare a un oggetto esistente all'interno dell'ambito di tale connessione. Ad esempio, nella struttura ad albero degli spazi dei nomi, se il **origine** proprietà contiene un URL assoluto, deve puntare a un nodo esistente all'interno dell'ambito del nodo identificato dall'URL nella stringa di connessione. Se il **origine** proprietà contiene un URL relativo, quindi viene convalidato all'interno del contesto di un'impostazione di **ActiveConnection** proprietà.  
  
 Il **origine** proprietà è di lettura/scrittura durante il **Record** oggetto viene chiuso ed è di sola lettura mentre il **Record** oggetto è aperto.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Proprietà Source (Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)

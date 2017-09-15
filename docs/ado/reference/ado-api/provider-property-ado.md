---
title: "Proprietà del provider (ADO) | Documenti Microsoft"
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
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1839d8bc9c954d3f5ceeafca2b604304801f643f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="provider-property-ado"></a>Proprietà del provider (ADO)
Indica il nome del provider per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che indica il nome del provider.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **Provider** proprietà per impostare o restituire il nome del provider per una connessione. Questa proprietà può anche essere impostata per il contenuto del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà o *ConnectionString* argomento del [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo; tuttavia, specificando un provider in più posizioni durante la chiamata di **aprire** metodo può produrre risultati imprevisti. Se viene specificato alcun provider, la proprietà utilizzerà MSDASQL ([il Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 Il **Provider** proprietà è di lettura/scrittura quando la connessione è chiusa e di sola lettura quando è aperto. L'impostazione non avrà effetto fino al è aprire il **connessione** oggetto o accesso di [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme del **connessione** oggetto. Se l'impostazione non è valido, si verifica un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà DefaultDatabase (VB) e di provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Esempio di proprietà DefaultDatabase (VB) e di provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md)

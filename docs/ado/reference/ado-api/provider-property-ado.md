---
title: Proprietà del provider (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22ee1b88ee6065a49c53ae7024c93e869099ca3a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755289"
---
# <a name="provider-property-ado"></a>Proprietà Provider (ADO)
Indica il nome del provider per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce un **stringa** valore che indica il nome del provider.  
  
## <a name="remarks"></a>Note  
 Usare la **Provider** proprietà per impostare o restituire il nome del provider per una connessione. Questa proprietà può essere impostata anche dal contenuto del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà o il *ConnectionString* argomento del [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo; tuttavia, specificando un provider in più di un'unica posizione durante la chiamata di **aperto** metodo può produrre risultati imprevisti. Se viene specificato alcun provider, la proprietà di impostazione predefinita sarà MSDASQL ([Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 Il **Provider** è di lettura/scrittura quando la connessione è chiusa e di sola lettura quando è aperto. L'impostazione ha effetto fino ad aprire il **connessione** oggetto o l'accesso di [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta del **connessione** oggetto. Se l'impostazione non è valida, si verifica un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà DefaultDatabase (VB) e provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Esempio di proprietà DefaultDatabase (VB) e provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)

---
title: Metodo OpenSchema | Documenti Microsoft
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
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c613ec5782f0bb9d2df0bbd1fa5990343fc8cada
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="openschema-method"></a>Metodo OpenSchema
Ottiene informazioni sullo schema di database dal provider.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto che contiene informazioni sullo schema. Il **Recordset** verrà aperto un cursore statico di sola lettura. Il *QueryType* determina le colonne visualizzate nel **Recordset**.  
  
#### <a name="parameters"></a>Parametri  
 *QueryType*  
 Qualsiasi [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) valore che rappresenta il tipo di query di schema per l'esecuzione.  
  
 *Criteri*  
 Facoltativa. Una matrice dei vincoli di query per ogni *QueryType* opzione, come indicato nella [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *SchemaID*  
 GUID per una query di schema provider non è definito dalla specifica OLE DB. Questo parametro è obbligatorio se *QueryType* è impostato su **adSchemaProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Il **OpenSchema** metodo restituisce autodescrittivo informazioni sull'origine dati, ad esempio quali sono le tabelle nell'origine dati, le colonne nelle tabelle e i tipi di dati supportati.  
  
 Il *QueryType* argomento è un GUID che indica le colonne (schemi) restituite. La specifica OLE DB include un elenco completo degli schemi.  
  
 Il *criteri* argomento limita i risultati di una query di schema. *Criteri* specifica una matrice di valori che deve verificarsi in un subset di colonne, denominate colonne di vincolo, nella finestra di corrispondente **Recordset**.  
  
 La costante **adSchemaProviderSpecific** viene utilizzato per il *QueryType* argomento se il provider definisce il proprio query dello schema non standard, oltre a quelle elencate in precedenza. Quando questa costante viene utilizzata, il *SchemaID* argomento è necessario passare il GUID della query dello schema da eseguire. Se *QueryType* è impostato su **adSchemaProviderSpecific** ma *SchemaID* non viene fornito, verrà generato un errore.  
  
 Provider non sono necessari per supportare tutte le query di schema standard OLE DB. In particolare, solo **adSchemaTables**, **adSchemaColumns**, e **adSchemaProviderTypes** sono necessari per la specifica OLE DB. Tuttavia, il provider non è necessario per supportare il *criteri* vincoli indicati in precedenza per tali query dello schema.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** il **OpenSchema** metodo non è disponibile in un client-side [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
> [!NOTE]
>  In Visual Basic, le colonne che dispongono di un intero senza segno a 4 byte (DBTYPE UI4) nel **Recordset** restituito dal **OpenSchema** metodo il **connessione** oggetto non è possibile da confrontare con le altre variabili. Per ulteriori informazioni sui tipi di dati OLE DB, vedere [tipi di dati in OLE DB (OLE DB)](http://msdn.microsoft.com/en-us/6039292f-74e0-49b2-b133-17bc117ebf6a) e [appendice a: tipi di dati](http://msdn.microsoft.com/en-us/e3a0533a-2196-4eb0-a31e-92fe9556ada6) in riferimento Microsoft OLE DB Programmer.  
  
> [!NOTE]
>  **Gli utenti di Visual C/C++** quando non si utilizzano cursori sul lato client, il recupero "ORDINAL_POSITION" di uno schema di colonna in ADO restituisce un valore variant di tipo VT_R8 in MDAC 2.7, MDAC 2.8 e Windows Data Access Components (Windows DAC) 6.0, mentre il tipo utilizzato in MDAC 2.6 è VT_I4. Programmi scritti per MDAC 2.6 che cerca solo una variante restituito di tipo che VT_I4 potrebbe ottenere il valore zero per ogni numero ordinale se eseguiti con MDAC 2.7, MDAC 2.8 e Windows DAC 6.0 senza modifiche. Sono state modificate perché il tipo di dati OLE DB restituisce DBTYPE_UI4 e il tipo VT_I4 con segno non c'è spazio sufficiente per contenere tutti i possibili valori senza troncamento eventualmente in corso e causando una perdita di dati.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo OpenSchema (VB)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [Esempio di metodo OpenSchema (VC + +)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)

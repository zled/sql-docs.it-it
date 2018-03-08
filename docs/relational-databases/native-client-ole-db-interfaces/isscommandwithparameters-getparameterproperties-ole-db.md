---
title: 'Isscommandwithparameters:: Getparameterproperties (OLE DB) | Documenti Microsoft'
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords: GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a157de9b398914ce7dd9648cfd5612ffbf48a6a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Restituisce una matrice di strutture di set di proprietà SSPARAMPROPS, un set di proprietà SSPARAMPROPS per ogni tipo definito dall'utente o parametro XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pcParams*[out] [in]  
 Puntatore alla memoria che contiene il numero di strutture SSPARAMPROPS restituite *prgParamProperties*.  
  
 *prgParamProperties*[out]  
 Puntatore alla memoria nel quale viene restituita una matrice di strutture SSPARAMPROPS. Il provider alloca memoria per le strutture e restituisce l'indirizzo per la memoria. il consumer rilascia la memoria con **IMalloc:: Free** quando non è più necessario le strutture. Prima di chiamare **IMalloc:: Free** per *prgParamProperties*, il consumer deve chiamare anche **VariantClear** per il *vValue* proprietà di ogni struttura DBPROP per evitare una perdita di memoria nei casi in cui la variante contiene un tipo riferimento (ad esempio BSTR). Se *pcParams* è zero nell'output o si verifica un errore diverso da DB_E_ERRORSOCCURRED, il provider non alloca alcuna memoria e assicura che *prgParamProperties* è un puntatore null nell'output.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il **GetParameterProperties** metodo restituisce gli stessi codici di errore OLE DB principale **ICommandProperties** metodo, ad eccezione di tale DB_S_ERRORSOCCURRED e DB_E_ERRORSOCCURED non può essere generato.  
  
## <a name="remarks"></a>Osservazioni  
 **Isscommandwithparameters:: Getparameterproperties** si comporta in modo coerente rispetto a **GetParameterInfo**. Se [isscommandwithparameters:: Setparameterproperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) o **SetParameterInfo** non è stato chiamato o è stato chiamato con cParams pari a zero, **GetParameterInfo** deriva le informazioni sui parametri e restituisce l'oggetto. Se **isscommandwithparameters:: Setparameterproperties** o **SetParameterInfo** sono stati chiamati per almeno un parametro, **isscommandwithparameters:: Getparameterproperties** restituisce proprietà solo per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** è stato chiamato. Se **isscommandwithparameters:: Setparameterproperties** viene chiamato dopo **isscommandwithparameters:: Getparameterproperties** o **GetParameterInfo**, le successive chiamate a **isscommandwithparameters:: Getparameterproperties** restituiscono i valori sottoposti a override per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** è stato chiamato.  
  
 La struttura SSPARAMPROPS viene definita nel modo seguente:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Membro|Descrizione|  
|------------|-----------------|  
|*iOrdinal*|Numero ordinale del parametro passato.|  
|*cPropertySets*|Il numero di strutture DBPROPSET in *rgPropertySets*.|  
|*rgPropertySets*|Puntatore alla memoria nel quale restituire una matrice di strutture DBPROPSET.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB ISSCommandWithParameters &#40; &#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  

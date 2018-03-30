---
title: 'Isscommandwithparameters:: Getparameterproperties (OLE DB) | Documenti Microsoft'
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcd93da8a4a40af97284ea787ebf359490ebd0c1
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
 Puntatore alla memoria nel quale viene restituita una matrice di strutture SSPARAMPROPS. Il provider alloca memoria per le strutture e restituisce l'indirizzo per la memoria, il consumer rilascia questa memoria con **IMalloc:: Free** quando non è più necessario le strutture. Prima di chiamare **IMalloc:: Free** per *prgParamProperties*, il consumer deve chiamare anche **VariantClear** per il *vValue* proprietà ogni struttura DBPROP per evitare una perdita di memoria nei casi in cui la variante contiene un riferimento di tipo, ad esempio BSTR. Se *pcParams* è zero nell'output o si verifica un errore diverso da DB_E_ERRORSOCCURRED, il provider non alloca alcuna memoria e assicura *prgParamProperties* è un puntatore null nell'output.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il **GetParameterProperties** metodo restituisce gli stessi codici di errore OLE DB principali **ICommandProperties** metodo, ad eccezione di tale DB_S_ERRORSOCCURRED e DB_E_ERRORSOCCURED non può essere generato.  
  
## <a name="remarks"></a>Osservazioni  
 **Isscommandwithparameters:: Getparameterproperties** metodo funziona in modo coerente rispetto a **GetParameterInfo**. Se [isscommandwithparameters:: Setparameterproperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) oppure **SetParameterInfo** non è stato chiamato o è stato chiamato con cParams pari a zero, **GetParameterInfo**deriva le informazioni sui parametri e lo restituisce. Se **isscommandwithparameters:: Setparameterproperties** oppure **SetParameterInfo** sono stati chiamati per almeno un parametro, **isscommandwithparameters:: Getparameterproperties**  metodo restituisce proprietà solo per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** è stato chiamato. Se **isscommandwithparameters:: Setparameterproperties** viene chiamato dopo **isscommandwithparameters:: Getparameterproperties** oppure **GetParameterInfo**, le chiamate successive alle **isscommandwithparameters:: Getparameterproperties** restituiscono i valori sottoposti a override per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** metodo è stato chiamato.  
  
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
 [OLE DB ISSCommandWithParameters &#40; &#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  

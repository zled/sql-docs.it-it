---
title: 'Isscommandwithparameters:: Getparameterproperties (OLE DB) | Documenti Microsoft'
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
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
manager: craigg
ms.openlocfilehash: 9c0f35cd59a670e35db6400f681187c52e4b97ef
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689994"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
 Puntatore alla memoria nel quale viene restituita una matrice di strutture SSPARAMPROPS. Il provider alloca memoria per le strutture e restituisce l'indirizzo per la memoria, il consumer rilascia questa memoria con **IMalloc:: Free** quando non è più necessario le strutture. Prima di chiamare **IMalloc:: Free** per *prgParamProperties*, il consumer deve chiamare anche **VariantClear** per il *vValue* proprietà ogni struttura DBPROP per impedire una perdita di memoria nei casi in cui la variante contiene un riferimento di tipo, ad esempio BSTR. Se *pcParams* è zero nell'output o si verifica un errore diverso da DB_E_ERRORSOCCURRED, il provider non alloca alcuna memoria e assicura *prgParamProperties* è un puntatore null nell'output.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il **GetParameterProperties** metodo restituisce gli stessi codici di errore OLE DB principali **ICommandProperties** metodo, ad eccezione di tale DB_S_ERRORSOCCURRED e DB_E_ERRORSOCCURED non può essere generato.  
  
## <a name="remarks"></a>Remarks  
 **Isscommandwithparameters:: Getparameterproperties** metodo funziona in modo coerente rispetto a **GetParameterInfo**. Se [isscommandwithparameters:: Setparameterproperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) oppure **SetParameterInfo** non è stato chiamato o è stato chiamato con cParams pari a zero, **GetParameterInfo**deriva le informazioni sui parametri e lo restituisce. Se **isscommandwithparameters:: Setparameterproperties** oppure **SetParameterInfo** sono stati chiamati per almeno un parametro, **isscommandwithparameters:: Getparameterproperties**  metodo restituisce proprietà solo per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** è stato chiamato. Se **isscommandwithparameters:: Setparameterproperties** viene chiamato dopo **isscommandwithparameters:: Getparameterproperties** oppure **GetParameterInfo**, le chiamate successive alle **isscommandwithparameters:: Getparameterproperties** restituiscono i valori sottoposti a override per i parametri per il quale **isscommandwithparameters:: Setparameterproperties** metodo è stato chiamato.  
  
 La struttura SSPARAMPROPS viene definita nel modo seguente:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Membro|Description|  
|------------|-----------------|  
|*iOrdinal*|Numero ordinale del parametro passato.|  
|*cPropertySets*|Il numero di strutture DBPROPSET in *rgPropertySets*.|  
|*rgPropertySets*|Puntatore alla memoria nel quale restituire una matrice di strutture DBPROPSET.|  
  
## <a name="see-also"></a>Vedere anche  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  

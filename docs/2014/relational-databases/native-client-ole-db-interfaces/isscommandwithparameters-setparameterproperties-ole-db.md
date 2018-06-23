---
title: 'Isscommandwithparameters:: Setparameterproperties (OLE DB) | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f17947c2b5eb0a8438c074ffca34dca728ae859a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066730"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
  Imposta le proprietà dei parametri per i singoli parametri in base al numero ordinale oppure imposta proprietà dei parametri bulk specificando una matrice di strutture SSPARAMPROPS.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Argomenti  
 *cParams*[in]  
 Il numero di SSPARAMPROPS le strutture nel *rgParamProperties* matrice. Se questo numero è zero, `ISSCommandWithParameters::SetParameterProperties` eliminerà tutte le proprietà che avrebbero potuto essere specificate per qualsiasi parametro nel comando.  
  
 *rgParamProperties*[in]  
 Matrice di strutture SSPARAMPROPS da impostare.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il `ISSCommandWithParameters::SetParameterProperties` metodo restituisce gli stessi codici di errore OLE DB principali **ICommandProperties:: SetProperties** metodo.  
  
## <a name="remarks"></a>Remarks  
 Le proprietà dei parametri con questo metodo è consentita per ogni parametro in base al numero ordinale oppure con una sola `ISSCommandWithParameters::SetParameterProperties` chiamare una volta la struttura SSPARAMPROPS è stata compilata dalla matrice di proprietà.  
  
 Il **SetParameterInfo** metodo deve essere chiamato prima di chiamare il `ISSCommandWithParameters::SetParameterProperties` metodo. Se si chiama `SetParameterProperties(0, NULL)`, si cancellano tutte le proprietà di parametro specificate, mentre se si chiama `SetParameterInfo(0,NULL,NULL)`, si cancellano tutte le informazioni di parametro che includono le proprietà che potrebbero essere associate a un parametro.  
  
 La chiamata `ISSCommandWithParameters::SetParameterProperties` per specificare le proprietà per un parametro che non è di tipo DBTYPE_XML o DBTYPE_UDT restituisce DB_E_ERRORSOCCURRED o DB_S_ERRORSOCCURRED e viene contrassegnato il *dwStatus* campo di tutte le proprietà DBPROP contenute nella struttura SSPARAMPROPS per tale parametro con DBPROPSTATUS_NOTSET. È necessario attraversare la matrice DBPROP di ogni proprietà DBPROPSET contenuta nella struttura SSPARAMPROPS per individuare il parametro al quale DB_E_ERRORSOCCURRED o DB_S_ERRORSOCCURRED fa riferimento.  
  
 Se `ISSCommandWithParameters::SetParameterProperties` viene chiamato per specificare le proprietà dei parametri cui informazioni non sono state impostate ancora con **SetParameterInfo**, il provider restituisce E_UNEXPECTED con il messaggio di errore seguente:  
  
 Impossibile chiamare il metodo SetParameterProperties per i parametri specificati senza chiamare prima il metodo SetParameterInfo. È necessario impostare le informazioni sui parametri prima di impostare le proprietà dei parametri stessi.  
  
 Se la chiamata a `ISSCommandWithParameters::SetParameterProperties` contiene alcuni parametri in cui le informazioni di parametro sono stata impostata e alcuni parametri in cui le informazioni di parametro non sono stata impostata, le proprietà dwStatus DBPROPSET del set di proprietà SSPARAMPROPS verranno restituite con DBSTATUS_NOTSET.  
  
 La struttura SSPARAMPROPS viene definita nel modo seguente:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Miglioramenti nel motore di database a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] consentire isscommandwithparameters:: Setparameterproperties ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da isscommandwithparameters:: Setparameterproperties nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [individuazione dei metadati](../native-client/features/metadata-discovery.md).  
  
|Membro|Description|  
|------------|-----------------|  
|*iOrdinal*|Numero ordinale del parametro passato.|  
|*cPropertySets*|Il numero di strutture DBPROPSET in *rgPropertySets*.|  
|*rgPropertySets*|Puntatore alla memoria nel quale restituire una matrice di strutture DBPROPSET.|  
  
## <a name="see-also"></a>Vedere anche  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
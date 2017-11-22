---
title: Metodo CreateRecordset (RDS) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords: CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a1bec5dc5b8c0e159755c9689aac0c9bfc40217
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="createrecordset-method-rds"></a>Metodo CreateRecordset (RDS)
Crea un oggetto vuoto, disconnesso [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Oggetto*  
 Una variabile oggetto che rappresenta un [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) o [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *ColumnsInfos*  
 A **Variant** matrice di attributi che definisce ogni colonna di **Recordset** creato. Ogni definizione di colonna contiene una matrice di quattro attributi obbligatori e un attributo facoltativo.  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|Nome|Nome dell'intestazione di colonna.|  
|Tipo|Intero del tipo di dati.|  
|Dimensione|Numero intero di larghezza in caratteri, indipendentemente dal tipo di dati.|  
|Supporto di valori Null|Valore booleano.|  
|Scala (facoltativa)|Questo attributo facoltativo definisce la scala per i campi numerici. Se questo valore viene omesso, verranno troncati a una scala di tre valori numerici. Precisione non è interessata, ma verrà troncato a tre il numero di cifre dopo il separatore decimale.|  
  
 Il set di matrici di colonna verrà quindi raggruppato in una matrice, che definisce il **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto business sul lato server è possibile popolare il valore risultante **Recordset** con dati da un provider di dati non OLE DB, ad esempio un sistema operativo file contenente le quotazioni di borsa.  
  
 La tabella seguente elenca i [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valori supportati dal **CreateRecordset** metodo. Il numero indicato è il numero di riferimento utilizzato per definire i campi.  
  
 Ognuno dei tipi di dati è di lunghezza fissa o variabile. Tipi a lunghezza fissa devono essere definiti con una dimensione di -1, perché la dimensione è predeterminata ed è ancora necessaria una definizione di dimensioni. Tipi di dati a lunghezza variabile consentono dimensioni compreso tra 1 e 32767.  
  
 Per alcuni dei tipi di dati della variabile, il tipo può essere assegnato al tipo indicato nella colonna di sostituzione. Non si vedranno le sostituzioni fino a dopo il **Recordset** creata e compilata. È quindi possibile controllare per il tipo di dati effettivi, se necessario.  
  
|Length|Costante|Number|Sostituzione|  
|------------|--------------|------------|------------------|  
|Fisso|**adTinyInt**|16||  
|Fisso|**adSmallInt**|2||  
|Fisso|**Tutti**|3||  
|Fisso|**adBigInt**|20||  
|Fisso|**adUnsignedTinyInt**|17||  
|Fisso|**adUnsignedSmallInt**|18||  
|Fisso|**adUnsignedInt**|19||  
|Fisso|**adUnsignedBigInt**|21||  
|Fisso|**adSingle**|4||  
|Fisso|**adDouble**|5||  
|Fisso|**adCurrency**|6||  
|Fisso|**adDecimal**|14||  
|Fisso|**adNumeric**|131||  
|Fisso|**adBoolean**|11||  
|Fisso|**adError**|10||  
|Fisso|**adGuid**|72||  
|Fisso|**adDate**|7||  
|Fisso|**adDBDate**|133||  
|Fisso|**adDBTime**|134||  
|Fisso|**adDBTimestamp**|135|7|  
|Variabile|**adBSTR**|8|130|  
|Variabile|**Famiglia**|129|200|  
|Variabile|**adVarChar**|200||  
|Variabile|**adLongVarChar**|201|200|  
|Variabile|**adWChar**|130||  
|Variabile|**adVarWChar**|202|130|  
|Variabile|**adLongVarWChar**|203|130|  
|Variabile|**adBinary**|128||  
|Variabile|**adVarBinary**|204||  
|Variabile|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo CreateRecordset (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Esempio di metodo CreateRecordset (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [Metodo CreateObject (Servizi Desktop remoto)](../../../ado/reference/rds-api/createobject-method-rds.md)




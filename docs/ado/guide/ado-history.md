---
title: ADO History | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.topic: article
helpviewer_keywords:
- ADO, what's new
ms.assetid: 667673f2-3151-432b-894a-3fc60b704ea4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 283d7ff395edf23668d1921e1f3f2c2e3c985446
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="ado-features-for-each-release"></a>Funzionalità di ADO per ogni versione
Questo argomento elenca le nuove funzionalità introdotte per ogni versione di ADO, ADO MD e ADOX.

## <a name="ado-60"></a>ADO 6.0
 ADO 6.0 è incluso in Windows Vista, come parte di Windows Data Access Components (Windows DAC) 6.0. ADO 6.0 è funzionalmente equivalente al ADO 2.8.

## <a name="ado-28"></a>ADO 2.8
 ADO 2.8 è stato incluso in Windows XP e Windows Server 2003, come parte di Microsoft Data Access Components (MDAC) 2.8. Una versione ridistribuibile di MDAC 2.8 è anche disponibile. Si noti che questa versione ridistribuibile deve essere installata solo in Windows 2000. ADO 2.8 risolve diversi aspetti relativi alla sicurezza:

 *Accesso alle unità disco rigido non è consentito all'esterno di un'area attendibile.*
Tra i domini di scripting che includono i siti non trusted, sono disabilitate le seguenti operazioni: **Stream.SaveToFile**, **Stream.LoadFromFile**, **Recordset. Save**, e **Open**, utilizzato in combinazione con il **adCmdFile** flag o con il Provider Microsoft OLE DB persistenza (MSPersist).

 **Open** *,***Recordset. Save** *,***Stream.SaveToFile** *, e* **Stream.LoadFromFile***operano su solo i file fisici.* 
Questi metodi, ora, verificare che gli handle di file scegliere solo i file fisici.

 **Recordset.ActiveCommand***restituisce un errore quando viene richiamato da una pagina HTML/ASP.* 
In questo modo il **comando** oggetto dall'uso improprio.

 *Quante***recordset***restituito da un nidificata***forma***comando ha un limite superiore.* 
Un comando shape annidato ora restituisce un massimo di 512 **recordset**. Ciò significa che un **forma** comando non può essere annidato a qualsiasi profondità. Al contrario, il livello di nidificazione massimo è 512, se i risultati di ogni comando in una singola (figlio) **Recordset**. Se, in qualsiasi livello, un **forma** comando restituisce più **recordset**, il livello di nidificazione massimo sarà meno di 512.

## <a name="ado-27"></a>ADO 2.7
 *supporto della piattaforma a 64 bit* ADO 2.7 introduce il supporto per processori a 64 bit.

## <a name="ado-26"></a>ADO 2.6
 **CubDef.GetSchemaObject***metodo* a partire da ADO 2.6, gli oggetti ADO MD possono essere recuperati utilizzando nomi univoci, come specificato dal [proprietà UniqueName (ADO MD)](../../ado/reference/ado-md-api/uniquename-property-ado-md.md).   Non è necessario conoscere i nomi degli oggetti padre e raccolte padre non è necessario essere popolati per recuperare un oggetto dello schema. Vedere [GetSchemaObject metodo (ADO MD)](../../ado/reference/ado-md-api/getschemaobject-method-ado-md.md).

 *Comando flussi* il **comando** oggetto supporta i comandi nel formato di flusso come alternativa all'utilizzo di **CommandText** proprietà. Il [(ADO) la proprietà CommandStream](../../ado/reference/ado-api/commandstream-property-ado.md) può essere utilizzato per specificare i modelli XML o updategram come il **comando** di input con il Provider Microsoft OLE DB per SQL Server.

 **Sottolinguaggio***proprietà* [sottolinguaggio](../../ado/reference/ado-api/dialect-property.md) è una nuova proprietà che definisce la sintassi e regole generali che il provider utilizzato per analizzare la stringa o nel flusso.  

 **Command. Execute***metodo* il [metodo Execute](../../ado/reference/ado-api/execute-method-ado-command.md) di ADO **comando** oggetto è stato migliorato per l'utilizzo di flussi di input e output.  

 *Campo statusvalues* se si riscontra un errore DB_E_ERRORSOCCURRED quando si modifica un **campo** di una **Recordset**, ADO ora compilerà il **Field.Status**proprietà con le informazioni sullo stato appropriato in modo che l'utente dispone di ulteriori informazioni sulla causa dell'errore. Vedere [proprietà Status (campo ADO)](../../ado/reference/ado-api/status-property-ado-field.md).

 **NamedParameters***proprietà* [NamedParameters](../../ado/reference/ado-api/namedparameters-property-ado.md) è una proprietà di nuovo il **comando** oggetto che indica che il provider deve utilizzare denominato parametri.  

 *Set di risultati nei flussi* ADO può restituire set di risultati da un'origine dati in un **flusso**, anziché da un **Recordset** oggetto. Utilizzando la versione più recente del Provider Microsoft OLE DB per SQL Server, è possibile ottenere i risultati XML dal provider eseguendo una query di "Per XML". Oggetto **flusso** che riceve il set di risultati può essere aperto con un comando "Per XML" come origine. Vedere [il recupero dei set di risultati in flussi](../../ado/guide/data/retrieving-resultsets-into-streams.md).

 *Singola riga resultset* di ADO **Record** oggetti possono ora essere aperto su una stringa di comando o **comando** oggetto che restituisce una riga di dati dal provider. Ciò comporta un miglioramento delle prestazioni con i provider MDAC 2.6. Vedere [Open (metodo) (Record ADO)](../../ado/reference/ado-api/open-method-ado-record.md).

## <a name="ado-25"></a>ADO 2.5
 **Record** *oggetto* ADO 2.5 introduce il **Record** oggetto da rappresentare e gestire una riga da un **Recordset** o un provider di dati o un oggetto che incapsula un dati semistrutturati e non strutturati, ad esempio un file o directory.

 **Flusso** *oggetto* ADO 2.5 introduce anche il **flusso** oggetto per rappresentare un flusso di dati binario o di testo.

 *Associazione URL* ADO 2.5 introduce l'uso di un URL, come alternativa a un testo stringa e un comando di connessione, come nomi di oggetti di archivio dati. Un URL può essere utilizzato con esistente **connessione** e **Recordset** oggetti, come con il nuovo **Record** e **flusso** oggetti.

 *Provider di dati che supportano associazione URL* ADO 2.5 supporta i provider OLE DB che riconoscono gli schemi URL. Questo include i Provider OLE DB per Internet Publishing, che accede al file system di Windows 2000 e riconosce lo schema HTTP esistente.

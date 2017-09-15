---
title: Oggetto DataControl (RDS) | Documenti Microsoft
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
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 32e23b9cbd8cb74a43c6de48e006d4931835bcec
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="datacontrol-object-rds"></a>Oggetto DataControl (RDS)
Associa una query di data [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a uno o più controlli (ad esempio, una casella di testo, un controllo griglia o una casella combinata) per visualizzare il **Recordset** dati in una pagina Web.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Osservazioni  
 L'ID di classe per il **RDS. DataControl** oggetto è 0-983A-00C04FC29E33 BD96C556 65A3 - 11 D.  
  
> [!NOTE]
>  Se si verifica un errore che un [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) o **RDS. DataControl** oggetto non caricare, assicurarsi che si sta utilizzando l'ID di classe corretto. La classe ID per questi oggetti sono stati modificati dalla versione 1.0 e 1.1. Tenere inoltre presente che è necessario impostare le colonne che ammettono valori null anche quando si utilizza il **RDS DataControl** oggetto.  
  
 Per uno scenario di base, è necessario impostare solo la **SQL**, **Connetti**, e **Server** le proprietà del **RDS. DataControl** oggetto, che chiama automaticamente l'oggetto business predefinito, [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md).  
  
 Tutte le proprietà di **RDS. DataControl** sono facoltativi, poiché gli oggetti di business personalizzata possono sostituire le relative funzionalità.  
  
> [!NOTE]
>  Se si esegue una query per più risultati, solo i primi [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene restituito. Se sono necessari più set di risultati, assegnare a ognuno al relativo oggetto **DataControl**. Un esempio di una query per più risultati potrebbe essere come segue:`"Select * from Authors, Select * from Topics"`  
  
 Aggiunta di "DFMode = 20;" alla stringa di connessione quando si utilizza il **RDS. DataControl** oggetto può migliorare le prestazioni del server quando si aggiornano i dati. Con questa impostazione, il **RDSServer** oggetto sul server utilizza una modalità meno risorse. Tuttavia, le funzionalità seguenti non sono disponibili in questa configurazione:  
  
-   Utilizzo di query con parametri.  
  
-   Recupero di informazioni di parametro o una colonna prima di chiamare il **Execute** metodo.  
  
-   Impostazione **Transact Updates** a **True**.  
  
-   Ottenere lo stato di riga.  
  
-   La chiamata di [Resync](../../../ado/reference/ado-api/resync-method.md) metodo.  
  
-   Aggiornamento (in modo esplicito o automatico) tramite il [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) proprietà.  
  
-   Impostazione **comando** o [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) proprietà.  
  
-   Utilizzando **adCmdTableDirect**.  
  
 Il **RDS. DataControl** oggetto viene eseguito in modalità asincrona, per impostazione predefinita. Se necessaria l'esecuzione sincrona per l'applicazione, impostare il [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) uguale al parametro **adcExecSync** e [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) parametro uguale a **adcFetchUpFront**, come illustrato nell'esempio seguente.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Utilizzare uno **RDS. DataControl** oggetto per collegare i risultati di una singola query a uno o più controlli visivi. Ad esempio, si supponga che il codice di una query che richiede dati dei clienti, ad esempio nome, residenza, luogo di nascita, età e stato di priorità del cliente. È possibile usare una singola **RDS. DataControl** oggetto per visualizzare un cliente nome Age e Region in tre caselle di testo separato. Stato di priorità cliente in una casella di controllo. e tutti i dati in un controllo griglia.  
  
 Utilizzare diversi **RDS. DataControl** oggetti a cui collegarsi i risultati delle query più controlli visivi diversi. Si supponga, ad esempio, che è possibile utilizzare una query per ottenere informazioni relative a un cliente e una seconda query per ottenere informazioni sui prodotti che il cliente ha acquistato. Per visualizzare i risultati della prima query in tre caselle di testo e una casella di controllo e i risultati della query secondo in un controllo griglia desiderato. Se si utilizza l'oggetto business predefinito (**RDSServer**), è necessario eseguire le operazioni seguenti:  
  
-   Aggiungere due **RDS. DataControl** oggetti alla pagina Web.  
  
-   Scrittura di due query, uno per ogni **SQL** proprietà dei due **RDS. DataControl** oggetti. Uno **RDS. DataControl** oggetto conterrà una query SQL che richiede informazioni sul cliente; il secondo conterrà una query che richiede un elenco di prodotti, il cliente ha acquistato.  
  
-   Nel tag OBJECT di ogni controllo associato, specificare il valore DATAFLD per impostare i valori per i dati che si desidera visualizzare in ogni controllo visual.  
  
 Non vi è alcuna restrizione numero al numero di **RDS. DataControl** gli oggetti che è possibile incorporare utilizzando tag OBJECT in una singola pagina Web.  
  
 Quando si definisce la **RDS. DataControl** oggetto in una pagina Web, usare diverso da zero **altezza** e **larghezza** valori, ad esempio 1 (per evitare l'inclusione di spazio aggiuntivo).  
  
 Componenti client di servizio dati remoti sono già inclusi come parte di Internet Explorer 4.0; Pertanto, non è necessario includere un parametro CODEBASE nel **RDS. DataControl** tag object.  
  
 Con Internet Explorer 4.0 o versioni successive, è possibile associare ai dati tramite i controlli HTML e ActiveX® solo se sono contrassegnati come controlli del modello di apartment.  
  
> [!NOTE]
>  **Gli utenti di Microsoft Visual Basic** il **RDS. DataControl** è sicuro per gli script e viene usato solo nelle applicazioni basate sul Web. Un'applicazione client di Visual Basic ha non è più necessaria.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto DataControl (RDS), metodi ed eventi](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di oggetto DataControl (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)
























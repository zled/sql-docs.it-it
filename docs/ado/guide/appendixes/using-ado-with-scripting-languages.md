---
title: Utilizzo di ADO con linguaggi di Scripting | Documenti Microsoft
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
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3187ca8ddc47f4a48e982a5061d429a7f7a5738
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="using-ado-with-scripting-languages"></a>Utilizzo di ADO con linguaggi di Scripting
All'interno di un ambiente di scripting, ADO consente di esporre i dati tramite gli script sul lato server. In questo scenario, ADO, il provider OLE DB sottostante che viene utilizzato e vengono installati i componenti necessari per fare riferimento a un archivio dati specificato in un server che esegue Internet Information Services (IIS). Utilizzando le pagine ASP (Active Server), ADO è un componente a cui fa riferimento in uno script che può generare HTML, ad esempio. Questo contenuto HTML può essere passato tramite HTTP a un Web browser client. Usando gli script, la pagina Web per inviare le azioni allo script sul lato server, che consente di aggiornare, attraversare o visualizzare i dati specifici.  
  
 Prima di utilizzare un oggetto ActiveX in una pagina Web, è importante sapere se l'oggetto sicuro per lo script. Quando un oggetto è considerato sicuro per lo scripting, significa che il controllo non è possibile eseguire le azioni dannose nel computer dell'utente e pertanto può essere eseguito senza richiedere l'approvazione dell'utente. Nella tabella seguente sono elencati gli oggetti ADO e indica se sono sicuri per lo script.  
  
|Oggetto|Per lo Scripting è sicuro?|  
|------------|-------------------------|  
|Connessione ADO|Sì|  
|Comando ADO|no|  
|Parametro ADO|no|  
|Recordset ADO|Sì|  
|Record ADO|Sì|  
|Flusso ADO|Sì|  
|Errore ADO|no|  
|Catalogo ADOX|no|  
|Set di celle ADOX|no|  
|DataControl di servizi desktop remoto|Sì|  
|DataSpace di servizi desktop remoto|Sì|  
|Data factory di servizi desktop remoto|no|  
  
 Nella tabella seguente sono elencati i provider inclusi con Windows DAC o MDAC e indica se sono sicuri per lo script.  
  
|Provider|Per lo Scripting è sicuro?|  
|--------------|-------------------------|  
|Con forme|Sì|  
|Rendere persistenti|Sì|  
|Remote|Sì|  
|Provider OLE DB per SQL Server (SQLOLEDB)|no|  
|Provider OLE DB per ODBC (MSDASQL)|no|  
  
## <a name="odbc-data-sources"></a>Origini dei dati ODBC  
 Una differenza rilevante tra codice ADO scripting e di script non è l'origine dati ODBC, se utilizzato. Per le applicazioni non di script, è possibile creare un DSN utente in Amministratore origine dati ODBC. Per gli script in esecuzione in IIS, è necessario creare un DSN di sistema. in caso contrario gli script non riconosce l'origine dati creata. Questo vale per qualsiasi applicazione ADO di script utilizzando il Provider Microsoft OLE DB per ODBC tramite Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Riferimento alla libreria ADO  
 Non è applicabile con linguaggi di scripting.  
  
## <a name="handling-events"></a>Gestione degli eventi  
 Non è applicabile con linguaggi di scripting.  
  
 Gli argomenti seguenti contengono informazioni più specifiche sull'utilizzo di ADO con linguaggi di scripting:  
  
-   [Programmazione ADO VBScript](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [Programmazione ADO JScript](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Utilizzo di ADO con Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Uso di ADO con Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   

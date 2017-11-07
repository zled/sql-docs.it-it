---
title: Impossibile aggiornare i dati per una connessione dati nella cartella di lavoro | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e92a6ac8d430b88c18ecae14c2a52771b566d39d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook"></a>Impossibile aggiornare i dati per una connessione dati della cartella di lavoro
  Per cartelle di lavoro di Excel contenenti dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services restituisce questo errore se viene inviata una richiesta di connessione a un server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] che non verrà completata.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Si applica a:|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Vedere di seguito.|  
|Testo del messaggio|Impossibile aggiornare i dati per una connessione dati della cartella di lavoro. Riprovare o contattare l'amministratore di sistema. Impossibile aggiornare le connessioni seguenti: Dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## <a name="explanation-and-resolution"></a>Spiegazione e risoluzione  
 Impossibile connettersi o caricare i dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in Excel Services. Di seguito sono riportate le condizioni che causano l'errore:  
  
 **Scenario 1: il servizio non è stato avviato**  
  
 L'istanza di SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) non è stata avviata. Una password scaduta determinerà l'arresto del servizio in esecuzione. Per ulteriori informazioni sulla modifica della password, vedere [Configurare gli account del servizio PowerPivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md) e [Avviare o arrestare un server Power Pivot per SharePoint](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md).  
  
 **Scenario 2a: apertura di una versione precedente della cartella di lavoro nel server**  
  
 La cartella di lavoro che si sta provando ad aprire potrebbe essere stata creata con la versione SQL Server 2008 R2 di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per Excel. Molto probabilmente, il provider di dati di Analysis Services specificato nella stringa di connessione dati non è presente sul computer che sta gestendo la richiesta.  
  
 In questo caso, sarà possibile trovare questo messaggio nel log ULS: "aggiornamento non riuscito per '[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]t dati" nella cartella di lavoro '\<URL cartella di lavoro >'", seguito da"Impossibile stabilire una connessione".  
  
 Per determinare la versione della cartella di lavoro, aprirla in Excel e controllare il provider di dati specificato nella stringa di connessione. In una cartella di lavoro SQL Server 2008 R2 viene utilizzato MSOLAP.4 come provider di dati.  
  
 Una soluzione alternativa al problema è l'aggiornamento della cartella di lavoro. In alternativa, è possibile installare librerie client della versione SQL Server 2008 R2 di Analysis Services nei computer fisici che eseguono [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint o Excel Services, [Installazione del provider OLE DB di Analysis Services nei server di SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
 **Scenario 2b: Excel Services è in esecuzione su un server applicazioni che dispone della versione errata delle librerie client**  
  
 Per impostazione predefinita, SharePoint Server 2010 installa la versione SQL Server 2008 del provider OLE DB per Analysis Services nei server applicazioni su cui è in esecuzione Excel Services. In una farm che supporta l'accesso ai dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , tutti i server fisici che eseguono applicazioni che richiedono dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , ad esempio Excel Services e [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, devono usare una versione successiva del provider di dati.  
  
 Server che eseguono [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint ottengono automaticamente il provider di dati OLE DB aggiornato. Ad altri server, quali quelli che eseguono un'istanza autonoma di Excel Services senza [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint sullo stesso computer, è necessario applicare una patch perché usino le librerie client più recenti. Per altre informazioni, vedere [Installazione del provider OLE DB di Analysis Services nei server di SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
 **Scenario 3: il controller di dominio non è disponibile**  
  
 Il problema può essere dovuto al fatto che non è disponibile alcun controller di dominio per la convalida dell'identità utente. Il controller di dominio viene richiesto da Claims nel Servizio token Windows per autenticare l'utente di SharePoint in ogni connessione. Claims nel Servizio token Windows non utilizza le credenziali memorizzate nella cache. Convalida l'identità utente per ogni connessione.  
  
 È possibile confermare la causa di questo errore visualizzando il file registro di SharePoint. Se nei registri di SharePoint è incluso il messaggio "Impossibile recuperare WindowsIdentity da IClaimsIdentity", l'identità utente non può essere autenticata.  
  
 Per risolvere questo problema, aggiungere il computer allo stesso dominio del server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] o installare un controller di dominio nel computer locale. La seconda soluzione, cioè l'installazione del controller di dominio, richiederà la creazione di account di dominio locali per tutti i servizi e gli utenti. Sarà necessario configurare gli account di servizio e le autorizzazioni di SharePoint per gli account definiti.  
  
 L'installazione di un controller di dominio nel computer è utile se si intende usare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint in uno stato offline. Per istruzioni dettagliate sull'uso di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] offline, vedere la voce del blog su come disconnettere il server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla rete all'indirizzo [http://www.powerpivotgeek.com](http://go.microsoft.com/fwlink/?LinkId=184241).  
  
 **Scenario 4: server instabile**  
  
 Uno o più servizi possono trovarsi in uno stato incoerente. In alcuni casi, l'esecuzione di IISRESET consentirà di risolvere il problema.  
  
  


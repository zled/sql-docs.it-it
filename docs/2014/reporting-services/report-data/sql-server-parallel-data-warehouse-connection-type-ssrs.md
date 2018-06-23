---
title: Tipo di connessione a SQL Server Parallel Data Warehouse (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3925fd3d-2aa1-4768-96ad-cfc2c0ba9283
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7a8ce540cb3ecf555e5abc22a1927482409bc582
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063774"
---
# <a name="sql-server-parallel-data-warehouse-connection-type-ssrs"></a>Tipo di connessione a SQL Server Parallel Data Warehouse (SSRS)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] è uno strumento warehouse dati scalabile che offre prestazioni e scalabilità tramite l'elaborazione parallela massiva. [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] Usa [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] database per l'archiviazione di dati e l'elaborazione distribuita.  
  
 Lo strumento consente di partizionare tabelle di database di grandi dimensioni in più nodi fisici, dove ogni nodo esegue la propria istanza di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Quando un report si connette a [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] per recuperare i dati del report, si connette al nodo di controllo che gestisce l'elaborazione delle query nell'appliance [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] . Una volta stabilita la connessione, non si noteranno differenze nell'utilizzo di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] all'interno e all'esterno di un ambiente [!INCLUDE[ssDW](../../../includes/ssdw-md.md)].  
  
 Per includere dati da [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] nel report, è necessario disporre di un set di dati che si basa su un'origine dati di report di tipo [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Parallel Data Warehouse. Questo tipo di origine dati incorporato è basato sul [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] estensione per i dati Parallel Data Warehouse. Questo tipo di origine dati può essere utilizzato per connettersi e recuperare dati da [!INCLUDE[ssDW](../../../includes/ssdw-md.md)].  
  
 Questa estensione per i dati supporta parametri multivalore, aggregazioni server e credenziali gestiti separatamente dalla stringa di connessione.  
  
 Per ulteriori informazioni, visitare il sito Web relativo a [SQL Server 2008 R2 Parallel Data Warehouse](http://go.microsoft.com/fwlink/?LinkId=150895).  
  
 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore Report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Stringa di connessione  
 Quando ci si connette a [!INCLUDE[ssDW](../../../includes/ssdw-md.md)], si esegue la connessione a un oggetto di database in uno strumento [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] . L'oggetto di database viene specificato in Progettazione query. Se non si specifica un database nella stringa di connessione, la connessione viene eseguita al database predefinito assegnato dall'amministratore. Contattare l'amministratore del database per ottenere le informazioni di connessione e le credenziali da utilizzare per connettersi all'origine dati. Nell'esempio di stringa di connessione seguente specifica il database di esempio **CustomerSales**, nel [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] accessorio:  
  
```  
HOST=<IP address>; database= CustomerSales; port=<port>  
```  
  
 Inoltre, per fornire le credenziali quali nome utente e password, viene utilizzata la finestra di dialogo **Proprietà origini dati** . Le opzioni `User Id` e `Password` vengono aggiunte automaticamente alla stringa di connessione, pertanto non è necessario digitarle come parte della stringa di connessione. L'interfaccia utente fornisce anche le opzioni per specificare l'indirizzo IP del nodo di controllo nel [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] accessorio e il numero di porta. Per impostazione predefinita, il numero di porta è 17000. La porta è configurabile da un amministratore e nella stringa di connessione potrebbe essere utilizzato un numero di porta diverso.  
  
 Per altre informazioni ed esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="Credentials"></a> Credenziali  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] fornisce la propria tecnologia di sicurezza per implementare e archiviare nomi utente e password. Non è possibile utilizzare l'autenticazione di Windows. Se si tenta di connettersi a [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] utilizzando l'autenticazione di Windows, si verificherà un errore.  
  
 Le credenziali devono essere sufficienti per accedere al database. A seconda della query, potrebbe essere necessario utilizzare altre autorizzazioni, ad esempio autorizzazioni sufficienti per accedere a tabelle e viste. Il proprietario dell'origine dati esterna deve configurare le credenziali sufficienti a fornire l'accesso in sola lettura agli oggetti di database di cui si necessita.  
  
 Da un client di creazione di report sono disponibili le opzioni seguenti per la specifica delle credenziali:  
  
-   Utilizzare un nome utente e una password archiviati. Per negoziare il doppio hop che si verifica quando il database contenente i dati del report è diverso dal server di report, selezionare le opzioni per utilizzare le credenziali come credenziali di Windows. È inoltre possibile scegliere di rappresentare l'utente autenticato dopo essersi connessi all'origine dati.  
  
-   Non sono necessarie credenziali. Per utilizzare questa opzione, è necessario aver configurato l'account di esecuzione automatica sul server di report. Per altre informazioni, vedere [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) nella [documentazione relativa a Reporting Services](http://go.microsoft.com/fwlink/?linkid=121312) nel sito msdn.microsoft.com.  
  
 Per altre informazioni, vedere [connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) oppure [specificare le credenziali in Generatore Report](../specify-credentials-in-report-builder.md).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Query"></a> Query  
 Una query consente di specificare quali dati recuperare per un set di dati del report.  
  
 Le colonne nel set di risultati per una query popolano la raccolta dei campi per un set di dati. Se la query restituisce più set di risultati, nel report viene elaborato solo il primo set di risultati. Per impostazione predefinita, se si crea una nuova query o si apre una query esistente che può essere rappresentata nella finestra Progettazione query con interfaccia grafica, è disponibile la progettazione query relazionale. È possibile specificare una query nei modi seguenti:  
  
-   Compilare una query in modo interattivo. Utilizzare la finestra Progettazione query relazionale in cui è visualizzata una vista gerarchica di tabelle, viste, stored procedure e altri elementi del database organizzati in base allo schema di database. Selezionare colonne da tabelle o viste. Limitare il numero di righe di dati da recuperare specificando i criteri di filtro, raggruppamento e aggregazione. Personalizzare il filtro quando il report viene eseguito impostando l'opzione del parametro.  
  
-   Digitare o incollare una query. Utilizzare la finestra Progettazione query basata su testo per immettere [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] testo direttamente, per incollare testo di query da un'altra origine, per immettere query complesse che non può essere compilata utilizzando la finestra Progettazione query relazionale o per immettere espressioni basate su query.  
  
-   Consente di importare una query esistente da un file o un report. Utilizzare il pulsante **Importa** da una finestra Progettazione query per individuare un file con estensione sql o rdl e importare una query.  
  
 Per altre informazioni, vedere [Interfaccia utente di Progettazione query relazionale &#40;Generatore report&#41;](relational-query-designer-user-interface-report-builder.md) e [Interfaccia utente di Progettazione query basata su testo &#40;Generatore report&#41;](text-based-query-designer-user-interface-report-builder.md).  
  
 La finestra Progettazione query basata su testo supporta la modalità [Text](#QueryText), in cui è possibile digitare i comandi di [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] per selezionare dati dall'origine dati.  
  
-   [Text](#QueryText)  
  
 È possibile utilizzare [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] con [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] e [!INCLUDE[tsql](../../../includes/tsql-md.md)] con [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. I due dialetti del linguaggio SQL sono molto simili. Le query scritte per il tipo di connessione all'origine dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in genere possono essere utilizzate per il tipo di connessione all'origine dati di [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] .  
  
 Una query che recupera dati del report da un database di grandi dimensioni, che include un data warehouse quale [!INCLUDE[ssDW](../../../includes/ssdw-md.md)], potrebbe generare un set di risultati con un numero di righe molto elevato, a meno che i dati vengano aggregati e riepilogati in modo da ridurre il numero di righe restituito dalla query. È possibile scrivere query che includono funzioni di aggregazione e raggruppamento tramite la finestra di Progettazione query con interfaccia grafica o basata su testo.  
  
 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] supporta la clausola, parola chiave e le aggregazioni fornite dalla finestra di Progettazione query per riepilogare i dati.  
  
 La finestra Progettazione query con interfaccia grafica usata da [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] fornisce il supporto predefinito per il raggruppamento e le aggregazioni per semplificare la scrittura di query che recuperano solo dati riepilogativi. Il [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] funzionalità del linguaggio sono: il GROUP BY clausola, parola chiave DISTINCT e gli aggregati quali SUM e COUNT. La finestra Progettazione query basata su testo fornisce supporto completo per il [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] linguaggio, inclusi il raggruppamento e aggregazioni.  
  
 Per altre informazioni su [!INCLUDE[tsql](../../../includes/tsql-md.md)], vedere la [Guida di riferimento a Transact-SQL &#40;Motore di database& #41;](/sql/t-sql/language-reference) nella [Documentazione online](http://go.microsoft.com/fwlink/?LinkId=141687) di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sul sito msdn.microsoft.com.  
  
###  <a name="QueryText"></a> Utilizzo di query di tipo Text  
 Nella finestra Progettazione query basata su testo, è possibile digitare i comandi [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] per definire i dati in un set di dati. Le query che consente di recuperare i dati dai [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] sono uguali a quelle utilizzate per recuperare dati da istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che non sono in esecuzione all'interno di un [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] dell'applicazione. Ad esempio, [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] query Seleziona i nomi di tutti i dipendenti con mansioni di Assistente marketing:  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 Fare clic sul pulsante **Esegui** (**!**) sulla barra degli strumenti per eseguire la query e visualizzare il set di risultati.  
  
 Per parametrizzare questa query, aggiungere un parametro di query. Modificare ad esempio la clausola WHERE nella stringa seguente:  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 Quando si esegue la query, i parametri del report corrispondenti ai parametri di query verranno creati automaticamente. Per ulteriori informazioni, vedere [Parametri di query](#Parameters) di seguito in questo argomento.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Parameters"></a> Parametri  
 Quando il testo della query contiene variabili di query o stored procedure con parametri di input, vengono generati automaticamente i parametri di query corrispondenti per il set di dati e i parametri di report per il report. Il testo della query non deve includere l'istruzione DECLARE per ogni variabile della query.  
  
 La query SQL seguente, ad esempio, crea un parametro di report denominato `EmpID`:  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 Per impostazione predefinita, ogni parametro del report dispone di tipo di dati Text e un set di dati creato automaticamente per fornire un elenco a discesa di valori disponibili. Dopo aver creato i parametri di report, potrebbe essere necessario modificare i valori predefiniti. Per altre informazioni, vedere [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Remarks"></a> Osservazioni  
  
###### <a name="platform-and-version-information"></a>Informazioni sulla piattaforma e sulla versione  
 Per altre informazioni sul supporto della piattaforma e della versione, vedere [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online](http://go.microsoft.com/fwlink/?linkid=121312) di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="HowTo"></a> Procedure  
 In questa sezione sono contenute istruzioni dettagliate per l'utilizzo di connessioni dati, origini dati e set di dati.  
  
 [Aggiungere e verificare una connessione dati o un'origine dati &#40;SSRS e Generatore Report&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Aggiungere un filtro a un set di dati &#40;Generatore report e SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Related"></a> Sezioni correlate  
 In queste sezioni della documentazione sono incluse informazioni concettuali approfondite sui dati dei report, nonché le procedure per definire, personalizzare e utilizzare parti di un report correlate ai dati.  
  
 [Aggiungere dati a un Report &#40;SSRS e Generatore Report&#41;](report-datasets-ssrs.md)  
 Viene fornita una panoramica sull'accesso ai dati del report.  
  
 [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Vengono fornite informazioni sulle connessioni dati e sulle origini dati.  
  
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sui set di dati incorporati e condivisi.  
  
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sulla raccolta di campi di set di dati generata dalla query.  
  
 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online](http://go.microsoft.com/fwlink/?linkid=121312) di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
 Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../2014-toc/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  

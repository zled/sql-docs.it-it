---
title: "Creazione di configurazioni dei pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di SQL Server Integration Services, configurazioni"
  - "Libreria configurazioni pacchetto - finestra di dialogo"
  - "pacchetti SSIS, configurazioni"
  - "pacchetti di Integration Services, configurazioni"
  - "configurazioni [Integration Services]"
  - "pacchetti [Integration Services], configurazioni"
  - "distribuzione di pacchetti [Integration Services], configurazioni"
ms.assetid: 91ac0347-f908-44f5-bd3d-115790223af4
caps.latest.revision: 72
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 72
---
# Creazione di configurazioni dei pacchetti
  Le configurazioni di pacchetto vengono create nella finestra di dialogo **Libreria configurazioni pacchetto** e con la Configurazione guidata pacchetto. Per accedere a questi strumenti, fare clic su **Configurazioni pacchetto** nel menu **SSIS** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
  
 **NOTE**
>Per accedere a **Libreria configurazioni pacchetto** è anche possibile fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **Configuration**. Quest'ultima viene visualizzata nella finestra delle proprietà del pacchetto.  
  
>Le configurazioni sono disponibili per il modello di distribuzione del pacchetto. I parametri vengono utilizzati al posto delle configurazioni per il modello di distribuzione del progetto. Con il modello di distribuzione del progetto è possibile distribuire i progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per altre informazioni sui modelli di distribuzione, vedere [Distribuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx).  
  
>Nella finestra di dialogo **Libreria configurazioni pacchetto** è possibile abilitare l'uso delle configurazione da parte dei pacchetti, aggiungere ed eliminare configurazioni, nonché impostare l'ordine preferito di caricamento delle configurazioni. 
 
>Il caricamento delle configurazioni di pacchetto nell'ordine preferito avviene a partire dall'inizio dell'elenco visualizzato nella finestra di dialogo **Libreria configurazioni pacchetto** fino alla fine dell'elenco. In fase di esecuzione, tuttavia, tali configurazioni potrebbero non essere caricate nell'ordine preferito. In particolare, le configurazioni di pacchetto padre vengono caricate dopo quelle di altri tipi.  
  
>Se più configurazioni impostano la stessa proprietà dell'oggetto, in fase di esecuzione viene utilizzato l'ultimo valore caricato.  
  
 Nella finestra di dialogo **Libreria configurazioni pacchetto** è possibile avviare la Configurazione guidata pacchetto tramite cui è possibile eseguire i vari passaggi necessari per la creazione di una configurazione. Per eseguire la Configurazione guidata pacchetto, aggiungere una nuova configurazione o modificarne una esistente nella finestra di dialogo **Libreria configurazioni pacchetto**. Nei passaggi della procedura guidata viene specificato il tipo di configurazione, viene impostato l'accesso alla configurazione in modo diretto o tramite variabili di ambiente e vengono selezionate le proprietà da salvare nella configurazione.  
  
 Nell'esempio seguente vengono illustrate le proprietà di destinazione di una variabile e di un pacchetto nel modo in cui vengono indicate nella pagina Completamento procedura guidata della Configurazione guidata pacchetto:  
  
 \Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]  
  
 \Package.Properties[MaximumErrorCount]  
  
 \Package.Properties[LoggingMode]  
  
 \Package.Properties[LocaleID]  
  
 \Package\My SQL Task.Variables[User::varTableName].Properties[Value]  
  
 In questo esempio, tramite la configurazione vengono aggiornate le proprietà seguenti:  
  
-   Proprietà RaiseChangedEvent della variabile definita dall'utente `TodaysDate`.  
  
-   Proprietà MaximumErrorCount, LoggingMode e LocaleID del pacchetto.  
  
-   Proprietà Value della variabile definita dall'utente `varTableName` nell'ambito dell'attività My SQL Task.  
  
 "\Package" rappresenta la radice, mentre gli oggetti che definiscono il percorso della proprietà aggiornata dalla configurazione sono separati da punti (.). I nomi di variabili e proprietà sono racchiusi tra parentesi quadre. Il termine Package è sempre utilizzato nella configurazione, indipendentemente dal nome del pacchetto. Per tutti gli altri oggetti inclusi nel percorso vengono tuttavia utilizzati i relativi nomi definiti dall'utente.  
  
 Al completamento della procedura guidata la nuova configurazione viene aggiunta all'elenco delle configurazioni nella finestra di dialogo **Libreria configurazioni pacchetto**.  
  
> **NOTA:** nell'ultima pagina di Configurazione guidata pacchetto, Completamento procedura guidata, sono elencate le proprietà di destinazione presenti nella configurazione. Per aggiornare le proprietà quando i pacchetti vengono eseguiti con l'utilità del prompt dei comandi **dtexec**, è possibile eseguire la Configurazione guidata pacchetto per generare le stringhe che rappresentano i percorsi delle proprietà e quindi copiarle e incollarle nella finestra del prompt dei comandi per usarle con l'opzione set di **dtexec**.  
  
 Nella tabella seguente vengono descritte le colonne dell'elenco delle configurazioni visualizzato nella finestra di dialogo **Libreria configurazioni pacchetto**.  
  
|Colonna|Description|  
|------------|-----------------|  
|**Nome configurazione**|Nome della configurazione.|  
|**Tipo configurazione**|Tipo di configurazione.|  
|**Stringa di configurazione**|Posizione della configurazione. La posizione può corrispondere a un percorso, a una variabile di ambiente, a una chiave del Registro di sistema, a un nome di variabile del pacchetto padre oppure a una tabella in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Oggetto di destinazione**|Nome dell'oggetto a cui è associata una proprietà con configurazione. Se la configurazione è un file di configurazione XML, la colonna è vuota in quanto questo tipo di configurazione può aggiornare più oggetti.|  
|**Proprietà di destinazione**|Nome della proprietà. Se tramite la configurazione si scrive in un file di configurazione XML o in una tabella di SQL Server, la colonna risulta vuota perché la configurazione può aggiornare più oggetti.|  
  
### Per creare una configurazione di pacchetto  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] fare clic sulla scheda **Flusso di controllo**, **Flusso di dati**, **Gestore evento** o **Esplora pacchetti**.  
  
4.  Scegliere **Configurazioni pacchetto** dal menu **SSIS**.  
  
5.  Nella finestra di dialogo **Libreria configurazioni pacchetto** selezionare **Abilita configurazioni pacchetto**, quindi fare clic su **Aggiungi**.  
  
6.  Nella pagina iniziale della Configurazione guidata pacchetto fare clic su **Avanti**.  
  
7.  Nel passaggio Selezione tipo di configurazione specificare il tipo di configurazione e impostare quindi le proprietà rilevanti per il tipo di configurazione specificato. Per altre informazioni, vedere [Riferimento all'interfaccia utente della Configurazione guidata pacchetti](../../integration-services/packages/package-configuration-wizard-ui-reference.md).  
  
8.  Nel passaggio Selezione proprietà da esportare selezionare le proprietà degli oggetti di pacchetto da includere nella configurazione. Se il tipo di configurazione selezionato supporta una sola proprietà, il titolo di questo passaggio della procedura guidata sarà Selezione proprietà di destinazione. Per altre informazioni, vedere [Riferimento all'interfaccia utente della Configurazione guidata pacchetti](../../integration-services/packages/package-configuration-wizard-ui-reference.md).  
  
    > **NOTA:** gli unici tipi di configurazione che supportano l'inserimento di più proprietà sono **File di configurazione XML** e **SQL Server**.  
  
9. Nel passaggio Completamento procedura guidata digitare il nome della configurazione, quindi fare clic su **Fine**.  
  
10. La configurazione sarà visibile nella finestra di dialogo **Libreria configurazioni pacchetto**.  
  
11. Scegliere **Chiudi**.  
  
## Risorse esterne  
  
-   Articolo tecnico [Understanding Integration Services Package Configurations](http://go.microsoft.com/fwlink/?LinkId=165643) (Informazioni sulle configurazioni dei pacchetti di Integration Services) sul sito Web msdn.microsoft.com  
  
-   Post di blog, [Creating packages in code – Package Configurations](http://go.microsoft.com/fwlink/?LinkId=217663) (Creazione di pacchetti in codice con configurazioni dei pacchetti), su www.sqlis.com.  
  
-   Post di blog [API Sample – Programmatically add a configuration file to a package](http://go.microsoft.com/fwlink/?LinkId=217664) (esempio di API relativo all'aggiunta a livello di programmazione di un file di configurazione a un pacchetto), su blogs.msdn.com.  
  
## Vedere anche  
 [Configurazioni di pacchetto](../../integration-services/packages/package-configurations.md)   
 [Distribuzione del pacchetto legacy &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)   
 [Utilizzo delle variabili a livello di programmazione](../../integration-services/building-packages-programmatically/working-with-variables-programmatically.md)  
  
  
---
title: Ruoli | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0662538b86f3d92c79b0426ac690c2b6f2f67152
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="roles"></a>Ruoli
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  I ruoli, nei modelli tabulari, consentono di definire le autorizzazioni dei membri per un modello. I membri del ruolo possono eseguire azioni sul modello, come definito dall'autorizzazione del ruolo. I ruoli definiti con autorizzazioni di lettura possono garantire inoltre sicurezza aggiuntiva a livello di riga tramite i relativi filtri. 
  
 Per SQL Server Analysis Services, i ruoli contengono membri di un utente dal nome utente di Windows o dal gruppo di Windows e le autorizzazioni (lettura, process, amministratore). Per Azure Analysis Services, gli utenti devono essere in Azure Active Directory e i nomi utente e i gruppi specificati devono essere dall'indirizzo di posta elettronica aziendale o UPN. 
  
> [!IMPORTANT]  
>  Per gli utenti di connettersi a un modello distribuito tramite un'applicazione client di creazione di report, è necessario creare almeno un ruolo con almeno l'autorizzazione a cui gli utenti sono membri di lettura.  
  
 In questo argomento sono destinate agli autori di modelli tabulari che definiscono i ruoli utilizzando la finestra di dialogo Gestione ruoli in SSDT. I ruoli definiti durante la creazione di modelli vengono applicati al database dell'area di lavoro modello. Dopo la distribuzione di un database modello, è possono gestire gli amministratori del database modello (aggiunta, modifica, eliminazione) i membri del ruolo utilizzando SQL Server Management Studio. Per informazioni su come gestire i membri dei ruoli in un database distribuito, vedere [ruoli nei modelli tabulari](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
##  <a name="bkmk_underst"></a> Understanding roles  
 I ruoli vengono utilizzati in Analysis Services per gestire l'accesso ai dati di modello. Sono disponibili due tipi di ruoli:  
  
-   Il ruolo di server, un ruolo fisso che fornisce l'accesso di amministratore a un'istanza del server Analysis Services.  
  
-   Ruoli del database, ovvero ruoli definiti dagli autori e amministratori di modelli per controllare l'accesso al database modello e ai dati per utenti non amministratori.  
  
 I ruoli definiti per un modello tabulare sono ruoli del database. Ovvero, i ruoli inclusi membri costituiti da utenti o gruppi che dispongono di autorizzazioni specifiche che definiscono l'azione di tali membri possono eseguire sul database modello. Un ruolo del database viene creato come oggetto separato nel database e viene applicato soltanto al database in cui è stato creato tale ruolo. Utenti e gruppi vengono inclusi nel ruolo dall'autore del modello, che, per impostazione predefinita, dispone delle autorizzazioni di amministratore sul server di database dell'area di lavoro. per un modello distribuito, da un amministratore.  
  
 I ruoli nei modelli tabulari possono essere definiti ulteriormente con filtri di riga. Per questi ultimi vengono utilizzate le espressioni DAX per definire le righe in una tabella e tutte le righe correlate nelle numerose direzioni in cui un utente può effettuare query. I filtri di riga tramite espressioni DAX possono essere definiti solo per le autorizzazioni di lettura e di lettura ed elaborazione. Per ulteriori informazioni, vedere [i filtri di riga](#bkmk_rowfliters) più avanti in questo argomento.  
  
 Per impostazione predefinita, quando si crea un nuovo progetto di modello tabulare, il progetto di modello non dispone di alcun ruolo. I ruoli possono essere definiti utilizzando la finestra di dialogo Gestione ruoli in SSDT. Quando i ruoli vengono definiti durante la creazione di modelli, essi vengono applicati al database dell'area di lavoro modello. Quando viene distribuito il modello, gli stessi ruoli vengono applicati al modello distribuito. Dopo la distribuzione di un modello, i membri del ruolo di server ([Analysis Services amministratore) e gli amministratori di database possono gestire i ruoli associati al modello e i membri associati a ogni ruolo utilizzando SQL Server Management Studio.  
  
##  <a name="bkmk_permissions"></a> Autorizzazioni  
 Ogni ruolo dispone di una singola autorizzazione definita per il database, eccetto l'autorizzazione combinata di lettura ed elaborazione. Per impostazione predefinita, un nuovo ruolo disporrà dell'autorizzazione Nessuno. Ovvero, una volta che i membri sono stati aggiunti al ruolo con l'autorizzazione Nessuno, non possono modificare il database, eseguire operazioni di elaborazione, eseguire query sui dati né esaminare il database, a meno che non venga concessa un'autorizzazione diversa.  
  
 Un gruppo o un utente può essere un membro di un numero qualsiasi di ruoli, ogni ruolo con un'autorizzazione diversa. Se un utente è membro di più ruoli, le autorizzazioni definite per ogni ruolo sono cumulative. Ad esempio, se un utente è membro di un ruolo con l'autorizzazione di lettura, e anche membro di un ruolo con l'autorizzazione Nessuno, tale utente disporrà delle autorizzazioni di lettura.  
  
 Ciascun ruolo può disporre di una delle seguenti autorizzazioni definite:  
  
|Autorizzazioni|Description|Filtri di riga tramite DAX|  
|-----------------|-----------------|----------------------------|  
|Nessuno|I membri non possono apportare alcuna modifica allo schema del database modello, né eseguire query sui dati.|Filtri di riga non applicabili. Agli utenti con questo ruolo non è visibile alcun dato.|  
|Lettura|I membri possono eseguire query sui dati, in base ai filtri di riga, ma non possono visualizzare il database modello in SSMS, né possono apportare modifiche allo schema del database modello e l'utente non può elaborare il modello.|Filtri di riga applicabili. Agli utenti sono visibili solo i dati specificati nella formula DAX del filtro di riga.|  
|Lettura ed elaborazione|I membri possono eseguire query sui dati in base ai filtri a livello di riga ed effettuare operazioni di elaborazione eseguendo uno script o un pacchetto contenente un comando di elaborazione, ma non possono apportare alcuna modifica al database, Non è possibile visualizzare il database modello in SQL Server Management Studio.|Filtri di riga applicabili. È possibile eseguire query solo sui dati specificati nella formula DAX del filtro di riga.|  
|Process|I membri possono effettuare operazioni di elaborazione eseguendo uno script o un pacchetto contenente un comando di elaborazione. Non è possibile modificare lo schema del database modello, Non è eseguire query sui dati. Impossibile eseguire query nel database modello in SQL Server Management Studio.|Filtri di riga non applicabili. Non è possibile eseguire query sui dati in questo ruolo|  
|Amministratore|I membri possono apportare modifiche allo schema del modello e possono eseguire una query tutti i dati in Progettazione modelli, report di client e SQL Server Management Studio.|Filtri di riga non applicabili. È possibile eseguire query su tutti i dati in questo ruolo.|  
  
##  <a name="bkmk_rowfliters"></a> Row filters  
 I filtri di riga consentono di definire su quali righe di una tabella i membri di un determinato ruolo possono eseguire query e vengono definiti per ogni tabella in un modello tramite formule DAX.  
  
 I filtri di riga possono essere definiti solo per ruoli con le autorizzazioni di lettura e di lettura ed elaborazione. Per impostazione predefinita, se per una particolare tabella non è stato definito alcun filtro di riga, i membri di un ruolo con l'autorizzazione di lettura o di lettura ed elaborazione saranno in grado di eseguire query su tutte le righe della tabella, a meno che non venga applicato il filtro incrociato da un'altra tabella.  
  
 Una volta definito un filtro di riga per una determinata tabella, una formula DAX da cui deve essere restituito un valore TRUE o FALSE, tale filtro consente di definire le righe in cui i membri di tale particolare ruolo possono eseguire query. Non sarà possibile eseguire query sulle righe non incluse nella formula DAX. Ad esempio, se nella tabella Customers è presente l'espressione dei filtri di riga seguente, *=Customers [Country] = “USA”*, i membri del ruolo relativo alle vendite potranno visualizzare solo i clienti negli Stati Uniti.  
  
 I filtri di riga vengono applicati alle righe specificate e a quelle correlate. Quando una tabella dispone di più relazioni, tramite i filtri viene applicata la sicurezza alla relazione che è attiva. I filtri di riga saranno intersecati con altri relativi filtri definiti per le tabelle correlate, ad esempio:  
  
|Tabella|Espressione DAX|  
|-----------|--------------------|  
|Region|=Region[Country]="USA"|  
|ProductCategory|=ProductCategory[Name]="Bicycles"|  
|Transazioni|=Transactions[Year]=2008|  
  
 Il risultato finale di queste autorizzazioni nella tabella Transactions è che i membri potranno eseguire query sulle righe di dati se il cliente si trova negli Stati Uniti, la categoria di prodotto è quella delle biciclette e l'anno è il 2008. Gli utenti non saranno in grado di eseguire query su alcuna transazione al di fuori degli Stati Uniti, che non riguardi biciclette o che non appartenga al 2008, a meno che non siano membri di un altro ruolo che garantisce tali autorizzazioni.  
  
 È possibile usare il filtro, *=FALSE()*, per negare l'accesso a tutte le righe per un'intera tabella.  
  
### <a name="dynamic-security"></a>Sicurezza dinamica  
 La sicurezza dinamica offre una modalità per definire la sicurezza a livello di riga in base al nome dell'utente attualmente connesso o alla proprietà CustomData restituita da una stringa di connessione. Per implementare la sicurezza dinamica, è necessario includere nel modello una tabella con i valori di accesso (nome utente di Windows) per gli utenti e un campo che è possibile utilizzare per definire una particolare autorizzazione; ad esempio, una tabella dimEmployees con un ID di accesso (dominio\nomeutente) e un valore di reparto per ogni dipendente.  
  
 Per implementare la sicurezza dinamica, è possibile utilizzare le funzioni seguenti come parte di una formula DAX per restituire il nome dell'utente attualmente connesso o la proprietà CustomData in una stringa di connessione:  
  
|Funzione|Description|  
|--------------|-----------------|  
|[Funzione USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)|Viene restituito il valore dominio\nomeutente dell'utente attualmente connesso.|  
|[Funzione CUSTOMDATA (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)|Viene restituita la proprietà CustomData in una stringa di connessione.|  
  
 È possibile utilizzare la funzione LOOKUPVALUE per restituire valori per una colonna in cui il nome utente di Windows corrisponde al nome utente restituito dalla funzione USERNAME o una stringa restituita dalla funzione CustomData. Le query possono quindi essere limitate nel caso in cui i valori restituiti da LOOKUPVALUE corrispondono ai valori nella stessa tabella o in una tabella correlata.  
  
 Ad esempio, utilizzando la formula:  
  
 `='dimDepartmentGroup'[DepartmentGroupId]=LOOKUPVALUE('dimEmployees'[DepartmentGroupId], 'dimEmployees'[LoginId], USERNAME(), 'dimEmployees'[LoginId], 'dimDepartmentGroup'[DepartmentGroupId])`  
  
 La funzione LOOKUPVALUE restituisce valori per la colonna dimEmployees[DepartmentId] dove dimEmployees[LoginId] corrisponde al valore LoginID dell'utente attualmente connesso, restituito da USERNAME e i valori per dimEmployees[DepartmentId] corrispondono ai valori per dimDepartmentGroup[DepartmentId]. I valori in DepartmentId restituiti da LOOKUPVALUE vengono quindi utilizzati per limitare le righe in cui vengono eseguite query nella tabella dimDepartment e qualsiasi tabella correlata da DepartmentId. Vengono restituite solo le righe in cui DepartmentId è presente anche nei valori per DepartmentId restituiti da LOOKUPVALUE.  
  
 **dimEmployees**  
  
|LastName|FirstName|LoginID|DepartmentName|DepartmentId|  
|--------------|---------------|-------------|--------------------|------------------|  
|Brown|Kevin|Adventure-works\kevin0|Marketing|7|  
|Bradley|David|Adventure-works\david0|Marketing|7|  
|Dobney|JoLynn|Adventure-works\JoLynn0|Production|4|  
|Baretto DeMattos|Paula|Adventure-works\Paula0|Human Resources|2|  
  
 **dimDepartment**  
  
|DepartmentId|DepartmentName|  
|------------------|--------------------|  
|1|Corporate|  
|2|Executive General and Administration|  
|3|Inventory Management|  
|4|Manufacturing|  
|5|Quality Assurance|  
|6|Research and Development|  
|7|Sales and Marketing|  
  
##  <a name="bkmk_testroles"></a> Testing roles  
 Quando si crea un progetto di modello, è possibile utilizzare la funzionalità Analizza in Excel in Progettazione modelli per eseguire un test circa l'efficacia dei ruoli definiti. Se si sceglie **Analizza in Excel** dal menu **Modello**in Progettazione modelli prima che venga aperto Excel, viene visualizzata la finestra di dialogo **Choose Credentials and Perspective** (Scegli credenziali e prospettiva). In questa finestra di dialogo è possibile specificare il nome utente corrente, un nome utente diverso, un ruolo e una prospettiva che verranno utilizzati per la connessione al modello dell'area di lavoro come origine dati. Per ulteriori informazioni, vedere [analizza in Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
##  <a name="bkmk_rt"></a> Related tasks  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare e gestire ruoli](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)|Nelle attività di questo argomento viene descritto come creare e gestire ruoli tramite la finestra di dialogo **Gestione ruoli** .|  
  
## <a name="see-also"></a>Vedere anche  
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Analizza in Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [Funzione USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [Funzione LOOKUPVALUE (DAX)](http://msdn.microsoft.com/en-us/73a51c4d-131c-4c33-a139-b1342d10caab)   
 [Funzione CUSTOMDATA (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  

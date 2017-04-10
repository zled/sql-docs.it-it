---
title: "Modificare il pool di account utente per SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Modificare il pool di account utente per SQL Server R Services
  Come parte del processo di installazione per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], un nuovo Windows *pool di account utente* viene creato per supportare l'esecuzione di attività tramite il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio. Lo scopo di questi account di lavoro consiste nell'isolare l'esecuzione simultanea di script R da diversi utenti SQL.
  
  Il numero di account utente in questo pool determina il numero di sessioni R che può essere attivo contemporaneamente.   Se lo stesso utente esegue contemporaneamente più script R, tutte le sessioni eseguita da tale utente utilizzerà lo stesso account di lavoro. Di conseguenza, un singolo utente potrebbe essere 100 script R diversi in esecuzione contemporaneamente, purché autorizzino le risorse.

## Configurazione di base   
-   In un'istanza predefinita, il nome del gruppo è **SQLRUserGroup**. 
-   In un'istanza denominata, il nome del gruppo predefinito presenta il suffisso con il nome dell'istanza: ad esempio, **SQLRUserGroupMyInstanceName**. 
-   Account: Per impostazione predefinita, il pool degli account utente contiene 20 gli account utente, denominati **MSSQLSERVER01** tramite **MSSQLSERVER20** per l'istanza predefinita.  
-   Per un'istanza denominata, gli account utente vengono denominati utilizzando il nome dell'istanza: ad esempio, **MyInstanceName01** tramite **MyInstanceName20**.  


## Gestione del gruppo di utenti per ogni istanza
Il gruppo di account Windows viene creato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione per ogni istanza in cui è installato Servizi di R, pertanto se è stato installato più istanze che supportano R, saranno presenti più gruppi di utenti.
Tuttavia, ogni gruppo di utenti è associato il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] in un'istanza specifica del servizio e non è in grado di supportare i processi R eseguiti in altre istanze.

Per impostazione predefinita, il gruppo non **non** dispone delle autorizzazioni di accesso per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza a cui è associato. Se è necessario per consentire l'esecuzione di script R dagli utenti, l'amministratore del database è necessario fornire questo gruppo con **connettersi** autorizzazioni.  

### Modificare il numero di account di lavoro nel gruppo di utenti Windows

Per modificare il numero di utenti nel pool di account, è necessario modificare le proprietà del [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] del servizio, come descritto di seguito.  
  
Le password associate a ciascun account utente vengono generate in modo casuale, ma è possibile modificarle in un secondo momento una volta creati gli account.  
  
1. Aprire Gestione configurazione SQL Server e selezionare **servizi di SQL Server**.
2. Fare doppio clic sul servizio Launchpad di SQL Server e arrestare il servizio se è in esecuzione. 
3.  Nel **servizio** scheda, verificare che la modalità di avvio sia impostata su automatico. Gli script R avrà esito negativo se la finestra di avvio non è in esecuzione.
4.  Fare clic su di **Avanzate** scheda e modificare il valore di **numero di utenti esterni** se necessario. Questa impostazione controlla il numero di utenti SQL diversi possono eseguire query simultaneamente in R. Il valore predefinito è 20 account, che nella maggior parte dei casi è più che sufficiente per supportare le sessioni di R.
5. Facoltativamente, è possibile impostare l'opzione **Reimposta Password agli utenti esterni** a _Sì_ Se l'organizzazione dispone di un criterio che richiede la modifica delle password ogni 90 giorni. Questa operazione verrà rigenerata le password crittografate che gestisce le finestra di avvio per gli account utente.    
6.  Riavviare il servizio.  

## Autorizzazioni aggiuntive necessarie per l'esecuzione di Script remoto
Se si esegue gli script R con il computer SQL Server remoto un contesto di calcolo, questo gruppo di lavoro deve disporre dell'autorizzazione per accedere all'istanza di SQL Server in cui verranno eseguiti gli script R.

Per ulteriori informazioni, vedere [domande frequenti su installazione e aggiornamento](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md). 

  
## Vedere anche  
 [Configurazione (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  
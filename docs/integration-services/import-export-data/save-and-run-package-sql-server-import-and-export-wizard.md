---
title: "Save and Run Package (SQL Server Import and Export Wizard) | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.saveschedule.f1"
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 69
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 65
---
# Save and Run Package (SQL Server Import and Export Wizard)
  Dopo aver specificato e configurato l'origine dati e la destinazione, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostra **Salvare ed eseguire il pacchetto**. In questa pagina specificare se eseguire immediatamente l'operazione di copia. A seconda della configurazione, è anche possibile salvare il pacchetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) creato dalla procedura guidata per personalizzarlo e usarlo di nuovo in seguito.
  
**Cos'è un pacchetto?** La procedura guidata usa SQL Server Integration Services (SSIS) per copiare i dati. In SSIS il pacchetto rappresenta l'unità di base. La procedura guidata crea un pacchetto SSIS in memoria mentre ci si sposta tra le pagine della procedura guidata e si specificano le opzioni.
  
## <a name="screen-shot-of-the-save-and-run-package-page"></a>Screenshot della pagina Salvare ed eseguire il pacchetto  
L'immagine seguente illustra la pagina **Salvare ed eseguire il pacchetto** della procedura guidata. 
   
![Save and run package page of the Import and Export Wizard](../../integration-services/import-export-data/media/save-and-run.png "Save and run package page of the Import and Export Wizard") 
  
## <a name="run-and-save-the-package"></a>Eseguire e salvare il pacchetto 
 Per continuare è necessario selezionare almeno una delle due opzioni seguenti.  
  
 **Esegui immediatamente**  
 Selezionare questa opzione per eseguire il pacchetto immediatamente.  
  
 **Salva pacchetto SSIS**  
 Salvare il pacchetto. In un secondo momento è facoltativamente possibile personalizzare il pacchetto ed eseguirlo nuovamente. Se si sceglie di salvare il pacchetto, sono disponibili opzioni aggiuntive nella pagina successiva, **Salva pacchetto SSIS**. L'opzione per salvare il pacchetto è disponibile solo se si usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition o un'edizione superiore.   
  
> [!NOTE] Se si completa la procedura guidata, si esegue il pacchetto e poi l'esecuzione del pacchetto viene arrestata prima del completamento, il pacchetto non verrà salvato, anche se si seleziona la casella di controllo **Salva** in questa pagina.  
  
## <a name="specify-options-for-saving-the-package"></a>Specificare le opzioni di salvataggio del pacchetto
**SQL Server**  
 Selezionare questa opzione per salvare il pacchetto nel database **msdb** nella tabella **sysssispackages**.
 
> [!NOTE] Questa opzione non salva il pacchetto nel database del catalogo SSIS (SSISDB).  

 È possibile selezionare il server di destinazione e fornire le credenziali per connettersi al server nella pagina successiva, **Salva pacchetto SSIS**. Per altre informazioni, vedere [Salva pacchetto SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
 **File system**  
 Selezionare questa opzione per salvare il pacchetto come file con estensione **dtsx**.  
  
 È possibile selezionare la cartella e il nome file di destinazione per il pacchetto nella pagina successiva, **Salva pacchetto SSIS**. Per altre informazioni, vedere [Salva pacchetto SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
 
 ## <a name="specify-the-package-protection-level"></a>Specificare il livello di protezione del pacchetto
 **Livello di protezione pacchetto**  
 Selezionare un livello di protezione dall'elenco per proteggere i dati nel pacchetto.  
  
 Il livello di protezione determina il metodo di protezione, la password o chiave utente e l'ambito di protezione del pacchetto. La protezione può includere tutti i dati o solo i dati sensibili. Per altre informazioni sulle opzioni disponibili, vedere [Access Control for Sensitive Data in Packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md).  
  
 **Password**  
 Digitare una password.  
  
 **Conferma password**  
 Digitare di nuovo la password.  
  
> [!NOTE] Le opzioni per la password sono disponibili solo se viene specificato un **Livello di protezione pacchetto** che richiede una password, ovvero **Crittografa tutti i dati sensibili con una password** o **Crittografa tutti i dati con una password**.  

## <a name="can-i-run-and-save-the-package"></a>È possibile eseguire e salvare il pacchetto?
 Il metodo che si usa per avviare la procedura guidata determina se è possibile eseguire e salvare il pacchetto creato tramite la procedura stessa. In alcuni casi l'opzione **Esegui** o **Salva** è disabilitata in questa pagina della procedura guidata.
 
|Come avviare la procedura guidata|È possibile eseguire il pacchetto?|È possibile salvare il pacchetto?|
|------------------------|------------------------|-------------------------|
|La procedura guidata si avvia dal menu Start, dal prompt dei comandi o da SQL Server Management Studio.|È possibile scegliere di avviare il pacchetto immediatamente al termine della procedura guidata, selezionando la casella di controllo **Esegui immediatamente**. Per impostazione predefinita, questa casella di controllo è selezionata e il pacchetto viene immediatamente eseguito.|Se si usa SQL Server Standard Edition o versione successiva, è possibile salvare il pacchetto facoltativamente.|
|Avviare la procedura guidata da un progetto di Integration Services in SQL Server Data Tools (SSDT).|Non è possibile eseguire il pacchetto se non dopo aver chiuso la procedura guidata. Quindi il pacchetto può essere eseguito in SQL Server Data Tools.|La procedura guidata salva il pacchetto nel progetto di Integration Services da cui la procedura stassa è stata avviata.|

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>Informazioni sulle due pagine di opzioni per il salvataggio del pacchetto  
 La pagina **Salvare ed eseguire il pacchetto** è una delle due pagine in cui è possibile selezionare le opzioni per il salvataggio del pacchetto SSIS.  
  
-   Nella pagina corrente è possibile scegliere di salvare il pacchetto in SQL Server o come file. È anche possibile selezionare le impostazioni di protezione per il pacchetto salvato.  
  
-   Quindi, nella pagina **Salva pacchetto SSIS** è possibile assegnare un nome al pacchetto e definire altre informazioni sulla posizione in cui salvarlo. Per altre informazioni, vedere [Salva pacchetto SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
 Queste opzioni sono disponibili solo se si seleziona l'opzione **Salva pacchetto SSIS** in questa pagina.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?  
 Dopo aver specificato se eseguire immediatamente l'operazione di copia e se si desidera salvare il pacchetto, la pagina successiva dipende dalle opzioni scelte.  
  
-   Se è stata selezionata l'opzione per eseguire il pacchetto immediatamente ma senza salvarlo, la pagina successiva è **Completamento procedura guidata**. In questa pagina è possibile rivedere le scelte effettuate nella procedura guidata e quindi avviare l'operazione di copia. Per altre informazioni, vedere [Completare la procedura guidata](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).  
  
-   Se è stata seleziona l'opzione per salvare il pacchetto, la pagina successiva è **Salva pacchetto SSIS**. In questa pagina è necessario specificare opzioni aggiuntive per il salvataggio del pacchetto. Quindi, dopo aver salvato il pacchetto, la pagina successiva è **Completamento procedura guidata**. Per altre informazioni, vedere [Salva pacchetto SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
## <a name="see-also"></a>Vedere anche  
[Salvare i pacchetti](../../integration-services/save-packages.md)  
[Eseguire pacchetti di Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
  

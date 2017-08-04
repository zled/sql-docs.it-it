---
title: Salva pacchetto SSIS (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 6ebbab742350e6874b86213c1fbf516e095a1e9a
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Salva pacchetto SSIS (Importazione/Esportazione guidata SQL Server)
  Se è specificato nel **Salva ed Esegui pacchetto** pagina che si desidera salvare le impostazioni come un pacchetto di SQL Server Integration Services (SSIS), il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata mostra **Salva pacchetto SSIS**. In questa pagina specificare opzioni aggiuntive per il salvataggio del pacchetto creato dalla procedura guidata.  

Le opzioni presenti nella pagina **Salva pacchetto SSIS** dipendono dalle scelte effettuate in precedenza nella pagina **Salvare ed eseguire il pacchetto** per salvare il pacchetto in SQL Server o nel file system. Per esaminare di nuovo la pagina **Salvare ed eseguire il pacchetto** , vedere [Salvare ed eseguire il pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).
 
**Cos'è un pacchetto?** La procedura guidata usa SQL Server Integration Services (SSIS) per copiare i dati. In SSIS il pacchetto rappresenta l'unità di base. La procedura guidata crea un pacchetto SSIS in memoria mentre ci si sposta tra le pagine della procedura guidata e si specificano le opzioni.

## <a name="screen-shot---common-options"></a>Schermata - opzioni comuni
La schermata seguente mostra la prima parte di **Salva pacchetto SSIS** pagina della procedura guidata. Il resto della pagina presenta un numero variabile di opzioni che variano a seconda della destinazione del pacchetto che si è scelto.

![Salva pacchetto - opzioni comuni](../../integration-services/import-export-data/media/save-package-common-options.png)

## <a name="provide-a-name-and-description-for-the-package"></a>Specificare un nome e una descrizione per il pacchetto  
 **Nome**  
 Consente di specificare un nome univoco per il pacchetto.  
  
 **Descrizione**  
 Consente di specificare una descrizione per il pacchetto. È consigliabile descrivere gli scopi del pacchetto, in modo da ottenere pacchetti autodocumentati più semplici da gestire.  
  
 **Destinazione**  
 La destinazione ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o file system) specificata in precedenza per il pacchetto. Per salvare il pacchetto in un'altra destinazione, tornare alla pagina **Salvare ed eseguire il pacchetto** .

## <a name="screen-shot---save-the-package-in-sql-server"></a>Screenshot del salvataggio del pacchetto in SQL Server

 L'immagine seguente mostra il **Salva pacchetto SSIS** pagina della procedura guidata se è stata selezionata la **SQL Server** opzione il **Salva ed Esegui pacchetto** pagina. 
  
![Salva pacchetto SSIS pagina dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/save-package2.png "pagina Salva pacchetto SSIS dell'importazione / esportazione guidata")  

## <a name="options-to-specify-target--sql-server"></a>Le opzioni per specificare (destinazione = SQL Server) 

 > [!NOTE]
 > La procedura guidata consente di salvare il pacchetto nel **msdb** database il **sysssispackages** tabella. Questa opzione non **non** salvare il pacchetto per il database del catalogo SSIS (SSISDB).  
 
 **Nome server**  
 Digitare o selezionare il nome del server di destinazione.  
   
 **Usa autenticazione di Windows**  
Connettersi al server tramite l'autenticazione integrata di Windows. Questo è il metodo di autenticazione ottimale.  
  
 **Usa autenticazione di SQL Server**  
Connettersi al server tramite l'autenticazione di SQL Server.  
  
 **Nome utente**  
Se è stata specificata l'autenticazione di SQL Server, immettere il nome utente.  
  
 **Password**  
Se è stata specificata l'autenticazione di SQL Server, immettere la password.  
    
## <a name="screen-shot---save-the-package-in-the-file-system"></a>Screenshot del salvataggio del pacchetto nel file system
 
L'immagine seguente mostra il **Salva pacchetto SSIS** pagina della procedura guidata se è stata selezionata la **File system** opzione il **Salva ed Esegui pacchetto** pagina. 
  
![Salva pacchetto SSIS pagina dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/save-package1.png "pagina Salva pacchetto SSIS dell'importazione / esportazione guidata")  

## <a name="options-to-specify-target--file-system"></a>Le opzioni per specificare (destinazione = File system)

 **Nome file**  
 Immettere il percorso e il nome del file di destinazione oppure utilizzare il **Sfoglia** pulsante per selezionare una destinazione.  
  
> [!TIP]
> Assicurarsi di specificare una cartella di destinazione per un elenco o tramite l'esplorazione. Se si immette solo il nome del file senza percorso, non si conosce in cui la procedura guidata consente di salvare il pacchetto. Inoltre, la procedura guidata potrebbe provare a salvare il pacchetto in un percorso di cui non dispone dell'autorizzazione per il salvataggio dei file e generare un errore.  
>   
>  Tenere presente la destinazione di salvataggio del file del pacchetto.  
  
 **Sfoglia**  
 Facoltativamente, esplorare per selezionare il percorso del file di destinazione nel **Salva pacchetto** la finestra di dialogo.  

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>Informazioni sulle due pagine di opzioni per il salvataggio del pacchetto  
 La pagina **Salva pacchetto SSIS** è una delle due pagine in cui è possibile selezionare le opzioni per il salvataggio del pacchetto SSIS.  
  
-   Nella pagina precedente, **Salvare ed eseguire il pacchetto**, è possibile scegliere di salvare il pacchetto in SQL Server o come file. È anche possibile selezionare le impostazioni di protezione per il pacchetto salvato. Per esaminare di nuovo la pagina **Salvare ed eseguire il pacchetto** , vedere [Salvare ed eseguire il pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  
  
-   Nella pagina corrente è possibile assegnare un nome al pacchetto e definire altre informazioni sulla posizione in cui salvarlo.  
 
## <a name="run-the-saved-package-again-later"></a>Esecuzione del pacchetto salvato in un secondo momento  
 Per informazioni su come eseguire il pacchetto salvato in un secondo momento, vedere uno gli argomenti seguenti.  
  
-   Per eseguire un pacchetto usando un'utilità con interfaccia utente semplice da usare, vedere [Guida di riferimento dell'interfaccia utente di Utilità di esecuzione pacchetti &#40;DtExecUI&#41;](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md).  
  
-   Per eseguire un pacchetto dalla riga di comando o da un file batch, vedere [Utilità dtexec](../../integration-services/packages/dtexec-utility.md).  
  
-   Se il pacchetto è stato salvato in SQL Server nel database **msdb** , connettersi al servizio Integration Services. In SQL Server Management Studio, in Esplora oggetti accedere a **Pacchetti archiviati | MSDB**, fare clic con il pulsante destro del mouse sul pacchetto e selezionare **Esegui pacchetto**.

-   Se il pacchetto è stato salvato nel file system, vedere [Eseguire pacchetti di Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md) per eseguire il pacchetto nell'ambiente di sviluppo. È necessario aggiungere il pacchetto a un progetto di Integration Services prima di poterlo aprire ed eseguire.  

## <a name="customize-the-saved-package"></a>Personalizzazione del pacchetto salvato  
 Per informazioni su come personalizzare il pacchetto salvato, vedere [Pacchetti di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md).  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver specificato le opzioni aggiuntive per il salvataggio del pacchetto, la pagina successiva è **Completare la procedura guidata**. In questa pagina è possibile rivedere le scelte effettuate nella procedura guidata, quindi di avviare l'operazione. Per altre informazioni, vedere [Completare la procedura guidata](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).  
 
## <a name="see-also"></a>Vedere anche  
[Salvare i pacchetti](../../integration-services/save-packages.md)  
[Eseguire pacchetti di Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
 


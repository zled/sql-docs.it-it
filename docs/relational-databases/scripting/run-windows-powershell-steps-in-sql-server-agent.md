---
title: Eseguire passaggi di Windows PowerShell in SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ae35fb3deecc8b77940ab76d1b0f016f00f39e27
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a>Esecuzione di passaggi di Windows PowerShell in SQL Server Agent
  Utilizzare SQL Server Agent per eseguire script di SQL Server PowerShell a orari pianificati.  
  
1.  **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)  
  
2.  **To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Sono disponibili molti tipi di passaggi del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Ogni tipo è associato a un sottosistema che implementa un ambiente specifico, ad esempio un agente di replica o un ambiente del prompt dei comandi. È possibile codificare gli script di Windows PowerShell, quindi utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per includere gli script nei processi eseguiti in base a orari pianificati o in risposta a eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È possibile eseguire gli script di Windows PowerShell con un passaggio del processo del prompt dei comandi o di PowerShell.  
  
1.  Usare un passaggio del processo di PowerShell per fare in modo che il sottosistema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent esegua l'utilità **sqlps** , che avvia PowerShell e importa il modulo **sqlps** .  
  
2.  Usare un passaggio del processo del prompt dei comandi per eseguire PowerShell.exe e specificare uno script che importa il modulo **sqlps** .  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
  
> [!CAUTION]  
>  Ogni passaggio del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent che esegue PowerShell con il modulo **sqlps** avvia un processo che utilizza all'incirca 20 MB di memoria. L'esecuzione simultanea di numerosi passaggi del processo di Windows PowerShell può avere un impatto negativo sulle prestazioni.  
  
##  <a name="PShellJob"></a> Creare un passaggio del processo di PowerShell  
 **Per creare un passaggio del processo di PowerShell**  
  
1.  Espandere **SQL Server Agent**, creare un nuovo processo oppure fare clic con il pulsante destro del mouse su un processo esistente e quindi scegliere **Proprietà**. Per ulteriori informazioni sulla creazione di un processo, vedere [Creazione di processi](http://msdn.microsoft.com/library/465fb7fc-7622-4252-a178-ea51691c935b).  
  
2.  Nella finestra di dialogo **Proprietà processo** fare clic sulla pagina **Passaggi** e quindi su **Nuovo**.  
  
3.  Nella finestra di dialogo **Nuovo passaggio di processo** digitare il nome del passaggio del processo nella casella **Nome passaggio**.  
  
4.  Scegliere **PowerShell** dall'elenco **Tipo**.  
  
5.  Nell'elenco **Esegui come** selezionare l'account proxy con le credenziali che verranno utilizzate dal processo.  
  
6.  Nella casella **Comando** immettere la sintassi dello script di PowerShell che verrà eseguito per il passaggio di processo. In alternativa, è possibile fare clic su **Apri** e selezionare un file contenente la sintassi dello script.  
  
7.  Fare clic sulla pagina **Avanzate** per impostare le opzioni seguenti relative al passaggio di processo: l'azione da eseguire in caso di esito positivo o negativo del passaggio, il numero di tentativi di esecuzione del passaggio che devono essere effettuati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e gli intervalli tra tentativi successivi.  
  
##  <a name="CmdExecJob"></a> Creare un passaggio del processo del prompt dei comandi  
 **Per creare un passaggio del processo di CmdExec**  
  
1.  Espandere **SQL Server Agent**, creare un nuovo processo oppure fare clic con il pulsante destro del mouse su un processo esistente e quindi scegliere **Proprietà**. Per ulteriori informazioni sulla creazione di un processo, vedere [Creazione di processi](http://msdn.microsoft.com/library/465fb7fc-7622-4252-a178-ea51691c935b).  
  
2.  Nella finestra di dialogo **Proprietà processo** fare clic sulla pagina **Passaggi** e quindi su **Nuovo**.  
  
3.  Nella finestra di dialogo **Nuovo passaggio di processo** digitare il nome del passaggio del processo nella casella **Nome passaggio**.  
  
4.  Nell'elenco **Tipo** selezionare **Sistema operativo (CmdExec)**.  
  
5.  Nell'elenco **Esegui come** selezionare l'account proxy con le credenziali che verranno utilizzate dal processo. Per impostazione predefinita, questi passaggi di processo vengono eseguiti nel contesto dell'account di servizio SQL Server Agent.  
  
6.  Nella casella **Elabora codice di uscita di un comando eseguito correttamente** digitare un valore compreso tra 0 e 999999.  
  
7.  Nella casella **Comando** , immettere powershell.exe con parametri che specificano lo script di PowerShell da eseguire.  
  
8.  Fare clic sulla pagina **Avanzate** per impostare le opzioni relative ai passaggi di processo, ad esempio l'operazione da eseguire se il passaggio di processo ha esito positivo o negativo, il numero di tentativi che devono essere eseguiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per l'esecuzione del passaggio di processo e il file in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può scrivere l'output del passaggio di processo. Solo i membri del ruolo predefinito del server **sysadmin** possono scrivere l'output dei passaggi di processo in un file di sistema operativo.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  

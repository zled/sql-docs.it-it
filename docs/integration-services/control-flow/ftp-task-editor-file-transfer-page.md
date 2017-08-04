---
title: "Editor attività FTP (pagina trasferimento File) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ca75f79962fcf7b7cae067a7d841f80f9c4c2032
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="ftp-task-editor-file-transfer-page"></a>Editor attività FTP (pagina Trasferimento file)
  Usare la pagina **Trasferimento file** della finestra di dialogo **Editor attività FTP** per configurare l'operazione FTP eseguita dall'attività.  
  
 Per altre informazioni su questa attività, vedere [Attività FTP](../../integration-services/control-flow/ftp-task.md).  
  
## <a name="options"></a>Opzioni  
 **IsRemotePathVariable**  
 Consente di specificare se il percorso remoto è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Selezionando il valore viene visualizzata l'opzione dinamica **RemoteVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Selezionando il valore viene visualizzata l'opzione dinamica **RemotePath**.|  
  
 **OverwriteFileAtDestination**  
 Consente di specificare se è possibile sovrascrivere un file nella destinazione.  
  
 **IsLocalPathVariable**  
 Consente di specificare se il percorso locale è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Selezionando il valore viene visualizzata l'opzione dinamica **LocalVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Selezionando il valore viene visualizzata l'opzione dinamica **LocalPath**.|  
  
 **Operazione**  
 Consente di selezionare l'operazione FTP da eseguire. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Invia file**|Consente di inviare i file. Selezionando questo valore vengono visualizzate le opzioni dinamiche **LocalVariable**, **LocalPathRemoteVariable** e **RemotePath**.|  
|**Ricevi file**|Consente di ricevere i file. Selezionando questo valore vengono visualizzate le opzioni dinamiche **LocalVariable**, **LocalPathRemoteVariable** e **RemotePath**.|  
|**Crea directory locale**|Consente di creare una directory locale. Selezionando questo valore vengono visualizzate le opzioni dinamiche **LocalVariable** e **LocalPath**.|  
|**Crea directory remota**|Consente di creare una directory remota. Selezionando questo valore vengono visualizzate le opzioni dinamiche **RemoteVariable** e **RemotelPath**.|  
|**Rimuovi directory locale**|Consente di rimuovere una directory locale. Selezionando questo valore vengono visualizzate le opzioni dinamiche **LocalVariable** e **LocalPath**.|  
|**Rimuovi directory remota**|Consente di rimuovere una directory remota. Selezionando questo valore vengono visualizzate le opzioni dinamiche **RemoteVariable** e **RemotePath**.|  
|**Elimina file locali**|Consente di eliminare file locali. Selezionando questo valore vengono visualizzate le opzioni dinamiche **LocalVariable** e **LocalPath**.|  
|**Elimina file remoti**|Consente di eliminare file remoti. Selezionando questo valore vengono visualizzate le opzioni dinamiche **RemoteVariable** e **RemotePath**.|  
  
 **IsTransferASCII**  
 Consente di specificare se i file ricevuti e inviati dal server FTP remoto devono essere trasferiti in modalità ASCII.  
  
## <a name="isremotepathvariable-dynamic-options"></a>Opzioni dinamiche di IsRemotePathVariable  
  
### <a name="isremotepathvariable--true"></a>IsRemotePathVariable = True  
 **RemoteVariable**  
 Selezionare una variabile definita dall'utente esistente oppure fare clic su \< **nuova variabile...** > per creare una variabile definita dall'utente.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), Aggiungi variabile  
  
### <a name="isremotepathvariable--false"></a>IsRemotePathVariable = False  
 **RemotePath**  
 Selezionare una gestione connessione FTP esistente o fare clic su \< **nuova connessione...** > per creare una gestione connessione.  
  
 **Argomenti correlati:** [Gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager.md), [Editor gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## <a name="islocalpathvariable-dynamic-options"></a>Opzioni dinamiche di IsLocalPathVariable  
  
### <a name="islocalpathvariable--true"></a>IsLocalPathVariable = True  
 **LocalVariable**  
 Selezionare una variabile definita dall'utente esistente oppure fare clic su \< **nuova variabile...** > per creare una variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), Aggiungi variabile  
  
### <a name="islocalpathvariable--false"></a>IsLocalPathVariable = False  
 **LocalPath**  
 Selezionare una gestione connessione File esistente oppure fare clic su \< **nuova connessione...** > per creare una gestione connessione.  
  
 **Argomenti correlati:** [Gestione connessione file flat](../../integration-services/connection-manager/flat-file-connection-manager.md), [Editor gestione connessione file flat](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività FTP &#40; Pagina generale &#41;](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  

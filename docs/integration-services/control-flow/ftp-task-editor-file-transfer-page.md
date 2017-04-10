---
title: "Editor attivit&#224; FTP (pagina Trasferimento file) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.filetransfer.f1"
helpviewer_keywords: 
  - "Editor attività FTP"
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor attivit&#224; FTP (pagina Trasferimento file)
  Usare la pagina **Trasferimento file** della finestra di dialogo **Editor attività FTP** per configurare l'operazione FTP eseguita dall'attività.  
  
 Per altre informazioni su questa attività, vedere [Attività FTP](../../integration-services/control-flow/ftp-task.md).  
  
## Opzioni  
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
  
## Opzioni dinamiche di IsRemotePathVariable  
  
### IsRemotePathVariable = True  
 **RemoteVariable**  
 Consente di selezionare una variabile esistente definita dall'utente o di creare una variabile definita dall'utente facendo clic su \<**Nuova variabile**>.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), Aggiungi variabile  
  
### IsRemotePathVariable = False  
 **RemotePath**  
 Consente di selezionare una gestione connessione FTP esistente o di creare una gestione connessione facendo clic su \<**Nuova connessione**>.  
  
 **Argomenti correlati:** [Gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager.md), [Editor gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## Opzioni dinamiche di IsLocalPathVariable  
  
### IsLocalPathVariable = True  
 **LocalVariable**  
 Consente di selezionare una variabile esistente definita dall'utente o di creare una variabile facendo clic su \<**Nuova variabile**>.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), Aggiungi variabile  
  
### IsLocalPathVariable = False  
 **LocalPath**  
 Consente di selezionare una gestione connessione file esistente o di creare una gestione connessione facendo clic su \<**Nuova connessione**>.  
  
 **Argomenti correlati:** [Gestione connessione file flat](../../integration-services/connection-manager/flat-file-connection-manager.md), [Editor gestione connessione file flat](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività FTP &#40;pagina Generale&#41;](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  
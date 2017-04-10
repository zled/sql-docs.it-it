---
title: "Editor attivit&#224; Message Queue (pagina Invio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msgqueuetask.send.f1"
helpviewer_keywords: 
  - "Editor attività Message Queue"
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# Editor attivit&#224; Message Queue (pagina Invio)
  Utilizzare la pagina **Invio** della finestra di dialogo **Editor attività Message Queue** per configurare un'attività Message Queue per l'invio di messaggi da un pacchetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Per ulteriori informazioni su questa attività, vedere [Message Queue Task](../../integration-services/control-flow/message-queue-task.md).  
  
## Opzioni  
 **UseEncryption**  
 Consente di indicare se crittografare il messaggio. Il valore predefinito è **False**.  
  
 **EncryptionAlgorithm**  
 Se si sceglie di utilizzare la crittografia, consente di specificare il nome dell'algoritmo di crittografia da utilizzare. L'attività Message Queue può utilizzare gli algoritmi RC2 e RC4. L'impostazione predefinita è **RC2**.  
  
> [!NOTE]  
>  L'algoritmo RC4 è supportato solo per motivi di compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. Nella versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.  
  
> [!IMPORTANT]  
>  Questi algoritmi di crittografia sono quelli supportati dalla tecnologia Microsoft Message Queuing (nota anche come MSMQ). Entrambi gli algoritmi di crittografia sono ormai considerati vulnerabili rispetto ad altri più recenti che tuttavia non sono ancora supportati da MSMQ. È pertanto consigliabile valutare con attenzione le esigenze di crittografia ai fini dell'invio di messaggi tramite l'attività Message Queue.  
  
 **MessageType**  
 Consente di selezionare il tipo di messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Messaggio file di dati**|Il messaggio viene archiviato in un file. La selezione del valore determina la visualizzazione dell'opzione dinamica **DataFileMessage**.|  
|**Messaggio variabili**|Il messaggio viene archiviato in una variabile. La selezione del valore determina la visualizzazione dell'opzione dinamica **VariableMessage**.|  
|**Messaggio stringa**|Il messaggio viene archiviato nell'attività Message Queue. La selezione del valore determina la visualizzazione dell'opzione dinamica **StringMessage**.|  
  
## Opzioni dinamiche di MessageType  
  
### MessageType = Messaggio file di dati  
 **DataFileMessage**  
 Consente di digitare il percorso del file di dati o di trovare il file usando il pulsante **(…)**.  
  
### MessageType = Messaggio variabili  
 **VariableMessage**  
 Consente di digitare i nomi delle variabili o di selezionare le variabili usando il pulsante **(…)**. Le variabili sono separate da virgole.  
  
 **Argomenti correlati:** Seleziona variabili  
  
### MessageType = Messaggio stringa  
 **StringMessage**  
 Consente di digitare il messaggio stringa direttamente o nella finestra di dialogo **Immettere il messaggio stringa** visualizzata facendo clic sul pulsante **(…)**.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Message Queue &#40;pagina Generale&#41;](../../integration-services/control-flow/message-queue-task-editor-general-page.md)   
 [Editor attività Message Queue &#40;pagina Ricezione&#41;](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  
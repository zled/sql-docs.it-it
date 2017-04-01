---
title: "Gestione dominio: elenco domini | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.dm.domainlist.f1"
ms.assetid: 8df305f0-97ea-4226-811b-979ed862e1f0
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Gestione dominio: elenco domini
  In questo argomento vengono descritti i controlli nell'elenco dei domini di **Gestione dominio** pagina [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Utilizzare questo riquadro per selezionare un dominio su cui eseguire le operazioni di gestione. Il riquadro stesso viene utilizzato per tutte le schede nel **Domain Management** pagina.  
  
## Opzioni  
  
### Elenco domini  
 **Dominio**  
 In questo elenco vengono visualizzati tutti i domini della Knowledge Base. Le operazioni che si eseguono nelle pagine a schede nel riquadro a destra saranno eseguite sul dominio selezionato nell'elenco. Per ulteriori informazioni, vedere  
  
 **Creazione di un dominio composito**  
 Consente di creare un nuovo dominio composito nella Knowledge Base. Questo comando Visualizza il **creare un dominio composito** la finestra di dialogo. Questo comando è disponibile facendo clic con il pulsante destro del mouse su un dominio o facendo clic sull'icona sopra l'elenco di domini. Per ulteriori informazioni, vedere [creare un dominio composito](../data-quality-services/create-a-composite-domain.md).  
  
 **Creazione di un dominio**  
 Consente di creare un nuovo dominio nella Knowledge Base. Questo comando Visualizza il **Crea dominio** la finestra di dialogo. Questo comando è disponibile facendo clic con il pulsante destro del mouse su un dominio o facendo clic sull'icona sopra l'elenco di domini. Per altre informazioni, vedere [Create a Domain](../data-quality-services/create-a-domain.md).  
  
 **Crea copia del dominio selezionato**  
 Consente di creare una copia esatta del dominio selezionato e di aggiungerla alla Knowledge Base. Il nome sarà il nome del dominio dal quale è stata creata la copia più " – Copy" aggiunto al nome. Questo comando è disponibile il pulsante destro del mouse a un dominio e quindi facendo clic su **creare una copia**, o facendo clic sull'icona sopra l'elenco di domini. Non è disponibile per un dominio composito.  
  
 **Importa dominio da file di dati**  
 Consente di importare un dominio da un file DQS. Questo comando Visualizza il **Importa da File di dati** la finestra di dialogo che consente di individuare il file system e selezionare un file DQS per un singolo dominio o un dominio composito. Questo comando è disponibile facendo clic sull'icona sopra l'elenco di domini. Per ulteriori informazioni, vedere [importare un dominio da un File DQS](../data-quality-services/import-a-domain-from-a-dqs-file.md).  
  
 **Elimina dominio**  
 Consente di eliminare il dominio selezionato dalla Knowledge Base. Questo comando Visualizza il **SQL Server Data Quality Services** la finestra di dialogo. Se si fa clic su **Sì**, il dominio e tutti i relativi dati verranno eliminati definitivamente. Questo comando è disponibile facendo clic con il pulsante destro del mouse su un dominio o facendo clic sull'icona sopra l'elenco di domini.  
  
 **Creazione di un dominio collegato**  
 Consente di creare un dominio collegato al dominio selezionato. Questo comando Visualizza il **Crea dominio** la finestra di dialogo. Questo comando è disponibile facendo clic su un dominio e quindi facendo clic su **creare un dominio collegato** collegato al dominio selezionato. Il dominio al quale si effettua il collegamento viene visualizzato nella finestra di dialogo Crea dominio. Il comando non è disponibile per un dominio composito. Non è previsto alcun comando per annullare il collegamento tra due domini. Per eseguire questa operazione, è necessario eliminare il dominio collegato. Non è possibile creare un dominio collegato a un dominio collegato. Per ulteriori informazioni, vedere [creare un dominio collegato](../data-quality-services/create-a-linked-domain.md).  
  
 Un dominio collegato dispone degli stessi valori del dominio al quale è stato collegato. Solo il nome e le proprietà del dominio sono diversi. Se si modificano una regola di dominio, un valore di dominio, un collegamento ai dati di riferimento o una relazione basata su termini nel dominio a cui è stato effettuato il collegamento, si modificheranno anche la regola di dominio, il valore di dominio, il collegamento ai dati di riferimento o la relazione basata su termini nel dominio collegato. Inoltre, se si modifica un valore nel dominio collegato, la modifica sarà apportata anche nel dominio a cui è stato effettuato il collegamento.  
  
 **Esporta Knowledge Base**  
 Consente di esportare l'intera Knowledge Base in un file DQS. Questo comando Visualizza il **esportare File di dati** la finestra di dialogo. Questo comando è disponibile facendo la **Esporta dati Knowledge Base** nella parte superiore della pagina o in **esportare** nel menu di scelta rapida dei domini nel riquadro dell'elenco di dominio. Per ulteriori informazioni, vedere [esportare una Knowledge Base in un File DQS](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).  
  
 **Esporta dominio**  
 Consente di esportare il dominio in un file DQS. Questo comando Visualizza il **esportare File di dati** la finestra di dialogo. Questo comando è disponibile nel **esportare** menu nella barra dei menu nella parte superiore della pagina o facendo clic sul riquadro dell'elenco di dominio. Per ulteriori informazioni, vedere [esportare un dominio in un File DQS](../data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
  
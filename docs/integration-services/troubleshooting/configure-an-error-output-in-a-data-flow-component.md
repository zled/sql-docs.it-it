---
title: "Configurazione di un output degli errori in un componente del flusso di dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errori [Integration Services], componenti flusso di dati"
  - "componenti [Integration Services], flusso di dati"
  - "output degli errori [Integration Services]"
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Configurazione di un output degli errori in un componente del flusso di dati
  Molti componenti del flusso di dati supportano l'output degli errori. A seconda del componente, in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] sono disponibili strumenti diversi per la configurazione di un output degli errori. Oltre a configurare un output degli errori, è possibile configurare le relative colonne, tra cui le colonne **ErrorCode** e **ErrorColumn** aggiunte dal componente.  
  
## Configurazione di un output degli errori  
 Per configurare un output degli errori sono disponibili due opzioni:  
  
-   Usare la finestra di dialogo **Configura output errori**. Questa finestra di dialogo consente di configurare un output degli errori in qualsiasi componente del flusso di dati che supporti l'output degli errori.  
  
-   Utilizzare la finestra di dialogo dell'editor per il componente. Alcuni componenti consentono di configurare gli output degli errori direttamente dalla finestra di dialogo dell'editor. Non è tuttavia possibile configurare output degli errori dalla finestra di dialogo dell'editor per l'origine ADO NET, la trasformazione Importa colonna, la trasformazione Comando OLE DB o la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Nelle procedure seguenti viene descritto come utilizzare queste finestre di dialogo per configurare gli output degli errori.  
  
#### Per configurare un output degli errori tramite la finestra di dialogo Configura output errori  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] fare clic sulla scheda **Flusso di dati**.  
  
4.  Trascinare l'output degli errori, rappresentato da una freccia rossa, dal componente corrispondente all'origine degli errori a un altro componente del flusso di dati.  
  
5.  Nella finestra di dialogo **Configura output errori** selezionare un'azione nelle colonne **Errore** e **Troncamento** per ogni colonna dell'input del componente.  
  
6.  Per salvare il pacchetto aggiornato, dal menu **File** scegliere **Salva elementi selezionati**.  
  
#### Per aggiungere un output degli errori tramite la finestra di dialogo dell'editor per il componente  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] fare clic sulla scheda **Flusso di dati**.  
  
4.  Fare doppio clic sui componenti del flusso di dati in cui si desidera configurare un output degli errori e, a seconda del componente, eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Configura output errori**.  
  
    -   Fare clic su **Output degli errori**.  
  
5.  Impostare l'opzione **Errore** per ogni colonna.  
  
6.  Impostare l'opzione **Troncamento** per ogni colonna.  
  
7.  Scegliere **OK**.  
  
8.  Per salvare il pacchetto aggiornato, dal menu **File** scegliere **Salva elementi selezionati**.  
  
## Configurazione delle colonne dell'output degli errori  
 Per configurare le colonne dell'output degli errori, è necessario usare la scheda **Proprietà input e output** della finestra di dialogo **Editor avanzato**.  
  
#### Per configurare le colonne dell'output degli errori  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] fare clic sulla scheda **Flusso di dati**.  
  
4.  Fare clic con il pulsante destro del mouse sul componente di cui si desidera configurare le colonne dell'output degli errori, quindi scegliere **Visualizza editor avanzato**.  
  
5.  Fare clic sulla scheda **Proprietà input e output**. Espandere **Output errori\> \<nome componente**, quindi **Colonne di output**.  
  
6.  Fare clic su una colonna e aggiornarne le proprietà.  
  
    > [!NOTE]  
    >  L'elenco di colonne include le colonne dell'input del componente, le colonne **ErrorCode** e **ErrorColumn** aggiunte dall'output degli errori precedente e le colonne **ErrorCode** e **ErrorColumn** aggiunte dal componente corrente.  
  
7.  Scegliere **OK.**  
  
8.  Per salvare il pacchetto aggiornato, dal menu **File** scegliere **Salva elementi selezionati**.  
  
## Vedere anche  
 [Gestione degli errori nei dati](../../integration-services/data-flow/error-handling-in-data.md)  
  
  
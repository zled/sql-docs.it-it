---
title: "Eseguire un pacchetto in SQL Server Data Tools | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di Integration Services, esecuzione"
  - "pacchetti SSIS, esecuzione"
  - "pacchetti [Integration Services], esecuzione"
  - "pacchetti di SQL Server Integration Services, esecuzione"
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Eseguire un pacchetto in SQL Server Data Tools
  I pacchetti vengono eseguiti in genere in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] durante lo sviluppo, il debug e il test di pacchetti. In Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] l'esecuzione dei pacchetti è sempre immediata.  
  
 Durante l'esecuzione di un pacchetto, in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] viene visualizzato lo stato dell'esecuzione nella scheda **Stato**. È possibile visualizzare l'ora di inizio e di fine del pacchetto e delle attività e contenitori del pacchetto, oltre a informazioni sulle attività o contenitori che hanno avuto esito negativo. Dopo l'esecuzione del pacchetto, nella scheda **Risultati esecuzione** sono disponibili le informazioni di run-time. Per altre informazioni, vedere la sezione "Report di stato" nell'argomento [Debug del flusso di controllo](../../integration-services/troubleshooting/debugging-control-flow.md).  
  
 **Distribuzione in fase di progettazione**. Quando si esegue un pacchetto in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], il pacchetto viene compilato e quindi distribuito in una cartella. Prima di eseguire il pacchetto è possibile specificare la cartella in cui deve essere distribuito. Se non si specifica alcuna cartella, per impostazione predefinita viene usata la cartella **bin**. Questo tipo di distribuzione è detto distribuzione in fase di progettazione.  
  
### Per eseguire un pacchetto in SQL Server Data Tools  
  
1.  In Esplora soluzioni, se la soluzione contiene più progetti, fare clic con il pulsante destro del mouse sul progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente il pacchetto e quindi scegliere **Imposta come oggetto di avvio** per impostare il progetto di avvio.  
  
2.  In Esplora soluzioni, se il progetto contiene più pacchetti, fare clic con il pulsante destro del mouse su un pacchetto e quindi scegliere **Imposta come oggetto di avvio** per impostare il pacchetto di avvio.  
  
3.  Per eseguire un pacchetto, attenersi a una delle procedure seguenti:  
  
    -   Aprire il pacchetto da eseguire e quindi fare clic sul pulsante **Avvia debug** sulla barra dei menu oppure premere F5. Al termine dell'esecuzione del pacchetto premere MAIUSC+F5 per tornare alla modalità progettazione.  
  
    -   In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto e quindi scegliere **Esegui pacchetto**.  
  
### Per specificare una cartella diversa per la distribuzione in fase di progettazione  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella del progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente il pacchetto da eseguire e quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo **Pagine delle proprietà di \<nome progetto>** fare clic su **Compila**.  
  
3.  Aggiornare il valore della proprietà OutputPath per specificare la cartella da usare per la distribuzione in fase di progettazione e quindi fare clic su **OK**.  
  
## Vedere anche  
 [Esecuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx)   
 [Pacchetti di Integration Services (SSIS)](https://msdn.microsoft.com/library/ms141134.aspx)  
  
  
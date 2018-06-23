---
title: 'Passaggio 1: Creazione di un nuovo progetto di Integration Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3237d8a39b1d53b60fca2fcd65da0619d74a6300
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156246"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Passaggio 1: Creazione di un nuovo progetto di Integration Services
  Il primo passaggio nella creazione di un pacchetto in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste nel creare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Questo progetto include i modelli per gli oggetti (origini dati, viste origini dati e pacchetti) utilizzati in una soluzione di trasformazione dei dati.  
  
 I pacchetti che verranno creati in questa esercitazione relativa a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] interpretano i valori dei dati dipendenti dalle impostazioni locali. Se il computer non è configurato per l'utilizzo dell'opzione Inglese (Stati Uniti) per le impostazioni locali, è necessario impostare proprietà aggiuntive nel pacchetto. I pacchetti utilizzati nelle lezioni 2-5 vengono copiati dal pacchetto creato nella lezione 1 e non è necessario aggiornare le proprietà dipendenti dalle impostazioni locali nei pacchetti copiati.  
  
> [!NOTE]  
>  Per questa esercitazione è richiesto Microsoft SQL Server Data Tools.  
>   
>  Per altre informazioni sull'installazione di SQL Server Data Tools, vedere [Scaricare SQL Server Data Tools](http://msdn.microsoft.com/data/hh297027).  
  
### <a name="to-create-a-new-integration-services-project"></a>Per creare un nuovo progetto di Integration Services  
  
1.  Fare clic sul menu **Start** , scegliere **Programmi**, **Microsoft SQL Server**, quindi **SQL Server Data Tools**.  
  
2.  Scegliere **Nuovo** dal menu **File**e fare clic su **Progetto** per creare un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Business Intelligence** in **Modelli installati**e selezionare **Progetto di Integration Services** nel riquadro **Modelli** .  
  
4.  Nella casella **Nome** impostare il nome predefinito su **SSIS Tutorial**. Facoltativamente, deselezionare la casella di controllo **Crea directory per soluzione** .  
  
5.  Accettare il percorso predefinito o fare clic su **Sfoglia** per individuare la cartella che si vuole usare. Nella finestra di dialogo **Percorso progetto** fare clic sulla cartella, quindi scegliere **Seleziona cartella**.  
  
6.  Fare clic su **OK**.  
  
     Per impostazione predefinita viene creato e aggiunto al progetto un pacchetto vuoto in Pacchetti SSIS, denominato **Package.dtsx**.  
  
7.  Nella barra degli strumenti **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Package.dtsx**, fare clic su **Rinomina**e rinominare il pacchetto predefinito in **Lesson 1.dtsx**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Passaggio 2: Aggiunta e configurazione di una gestione connessione File Flat](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
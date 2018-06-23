---
title: Implementazione di pacchetti figlio | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 85a9e6c93f0b1c3157f9814508ee4fb9263cd444
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171076"
---
# <a name="implementation-of-child-packages"></a>Implementazione di pacchetti figlio
  Quando si implementa il bilanciamento del carico tramite [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], i pacchetti figlio vengono installati su altri server per sfruttare il tempo di CPU o di server disponibile. Per creare ed eseguire i pacchetti figlio è necessario attenersi alla procedura seguente:  
  
-   Progettare i pacchetti figlio.  
  
-   Spostare i pacchetti sul server remoto.  
  
-   Creare sul server remoto un processo di SQL Server Agent contenente un passaggio che esegue il pacchetto figlio.  
  
-   Eseguire il debug e il test del processo di SQL Server Agent e dei pacchetti figlio.  
  
 Poiché non sono previste limitazioni, durante la progettazione dei pacchetti figlio è possibile inserire qualsiasi funzionalità nei pacchetti. Se tuttavia il pacchetto deve accedere a dati, è necessario verificare che il server in cui viene eseguito il pacchetto abbia accesso a tali dati.  
  
 Per identificare il pacchetto padre che esegue i pacchetti figlio, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fare clic con il pulsante destro del mouse sul pacchetto in Esplora soluzioni e quindi scegliere **Pacchetto punto di ingresso**.  
  
 Terminata la progettazione dei pacchetti figlio è necessario distribuirli nei server remoti.  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a>Spostamento dei pacchetti figlio nell'istanza remota  
 Esistono più modi per spostare pacchetti su altri server. È tuttavia consigliabile utilizzare i due metodi seguenti:  
  
-   Esportazione di pacchetti tramite [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   Distribuzione di pacchetti compilando un'utilità di distribuzione per il progetto contenente i pacchetti da distribuire, quindi esecuzione dell'Installazione guidata pacchetti per installare i pacchetti nel file system o in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [pacchetto di distribuzione &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).  
  
 È necessario ripetere la distribuzione su tutti i server remoti che si desidera utilizzare.  
  
## <a name="creating-the-sql-server-agent-jobs"></a>Creazione dei processi di SQL Server Agent  
 Dopo la distribuzione dei pacchetti figlio sui vari server, creare un processo di SQL Server Agent su ogni server che contiene un pacchetto figlio. Il processo di SQL Server Agent deve contenere un passaggio che esegue il pacchetto figlio quando viene chiamato l'agente del processo. I processi di SQL Server Agent non sono processi pianificati, ma eseguono i pacchetti figlio solo quando vengono chiamati dal pacchetto padre. Nella notifica dell'esito positivo o negativo restituita al pacchetto padre viene comunicato l'esito positivo o negativo del processo di SQL Server Agent, specificando se la chiamata a SQL Server Agent è avvenuta correttamente, ma non viene indicato l'esito positivo o negativo del pacchetto figlio oppure se quest'ultimo è stato eseguito.  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a>Debug dei processi di SQL Server Agent e dei pacchetti figlio  
 Per il test dei processi di SQL Server Agent e dei relativi pacchetti figlio è possibile utilizzare uno dei metodi seguenti:  
  
-   Eseguire ogni pacchetto figlio in Progettazione SSIS, scegliendo **Debug** / **Avvia senza eseguire debug**.  
  
-   Eseguire ogni singolo processo di SQL Server Agent sul relativo computer remoto, tramite [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], per verificare che il pacchetto venga eseguito.  
  
 Per informazioni su come risolvere i problemi legati all'esecuzione di pacchetti dai processi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, vedere l'articolo relativo a [un pacchetto SSIS che non viene eseguito quando si chiama il pacchetto SSIS da un passaggio di processo di SQL Server Agent](http://support.microsoft.com/kb/918760) nella [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base.  
  
 SQL Server Agent verifica l'accesso al sottosistema per un proxy e garantisce l'accesso al proxy a ogni esecuzione del relativo passaggio del processo.  
  
 In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]è possibile creare un proxy.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   Intervento nel blog [SSIS: l'accesso alle variabili in un pacchetto padre](http://go.microsoft.com/fwlink/?LinkId=257729), sul sito Web consultingblogs.emc.com.  
  
-   Intervento nel blog [SSIS: deve eseguire i pacchetti figlio in-process o out-of-process?](http://go.microsoft.com/fwlink/?LinkId=220819), sul sito Web consultingblogs.emc.com.  
  
  
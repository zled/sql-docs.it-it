---
title: Essentials del pacchetto SSIS | Documenti Microsoft
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
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1efb7be8739413ff1688888f66313cd792d54684
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158274"
---
# <a name="ssis-package-essentials"></a>Concetti di base sui pacchetti SSIS
  Un pacchetto è l'oggetto che consente di implementare la funzionalità [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per estrarre, trasformare e caricare i dati. Un pacchetto viene creato utilizzando la finestra di progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] oppure eseguendo Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o Creazione guidata progetto connessioni in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Per ulteriori informazioni [creare pacchetti in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) in Progettazione SSIS e [importazione guidata progetto](../../2014/integration-services/import-project-wizard.md).  
  
 Un pacchetto di base include i seguenti elementi:  
  
 **Elementi del flusso di controllo**  
 Questi elementi obbligatori eseguono varie funzioni, come fornire la struttura e controllare l'ordine di esecuzione degli elementi. Gli elementi del flusso di controllo principale sono attività, contenitori e vincoli di precedenza. In un pacchetto deve esserci almeno un elemento del flusso di controllo.  
  
 Per altre informazioni, vedere [Flusso di controllo](control-flow/control-flow.md).  
  
 **Elementi del flusso di dati**  
 Questi elementi facoltativi estraggono, modificano e caricano dati nelle origini dati. Gli elementi del flusso di dati principali sono origini, trasformazioni e destinazioni. Nel pacchetto non deve esserci alcun elemento del flusso di dati.  
  
 Per altre informazioni, vedere [Flusso di dati](data-flow/data-flow.md).  
  
 Per un esempio di come creare un pacchetto di base, vedere [lezione 1: creazione del progetto e un pacchetto di base](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Creare pacchetti in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)  
  
-   [Aggiungere o eliminare un'attività o un contenitore in un flusso di controllo](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Aggiungere o eliminare un componente in un flusso di dati](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>Contenuto correlato  
  
1.  Video, [Creazione di un pacchetto di base (video di SQL Server)](http://go.microsoft.com/fwlink/?LinkId=131023), nel sito MSDN.Microsoft.com  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi di integrazione &#40;SSIS&#41; pacchetti](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Vincoli di precedenza](control-flow/precedence-constraints.md)  
  
  
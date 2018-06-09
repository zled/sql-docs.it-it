---
title: Creare un progetto Visual c# SMO in Visual Studio .NET | Documenti Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 25e06aa3493b10e5a282fc5a709605eae18cb5fd
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34708319"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Come creare un progetto Visual c# SMO in Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In questa sezione viene descritto come compilare un'applicazione console SMO semplice.  
  
 In questo esempio vengono importati spazi dei nomi affinché il programma faccia riferimento ai tipi SMO. L'importazione del **agente** dello spazio dei nomi è facoltativo. Utilizzarla quando si scrive un programma che utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Il **comuni** dello spazio dei nomi è necessario per stabilire una connessione sicura per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il **SqlClient** dello spazio dei nomi viene utilizzato per elaborare gli errori di eccezione SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Creazione di un progetto Visual C# SMO in Visual Studio.NET  
  
1. Avviare Visual Studio
  
2. Nel **File** menu, fare clic su **New** e quindi **progetto**.  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .   
  
3. Nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **installato** riquadro, passare a **modelli**\\**Visual c#**\\**Windows** e selezionare **applicazione Console**.  
  
4. (Facoltativo) Nel **nome** testo, digitare il nome della nuova applicazione.  

5. Fare clic su **OK** per caricare il modello di applicazione console.  

6. Seguire le istruzioni in [l'installazione di SMO](installing-smo.md) per installare il pacchetto per il progetto fare riferimento.
  
7. Scegliere **Codice** dal menu **Visualizza**.
    
8. Nel codice, prima dell'istruzione dello spazio dei nomi, digitare quanto segue **utilizzando** istruzioni per qualificare i tipi nello spazio dei nomi SMO:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO dispone di vari spazi dei nomi in Microsoft.SqlServer.Management.Smo, ad esempio Microsoft.SqlServer.Management.Smo.Agent. Aggiungere questi spazi dei nomi poiché sono necessari.  
  
16. A questo punto è possibile aggiungere il codice SMO.  
  
  

---
title: 'Attività 4: Creazione di un progetto SSIS tramite SQL Server Data Tools | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a6fb09370b01a88c23d75b843d588626ed96c9b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208071"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Attività 4: Creazione di un progetto SSIS tramite SQL Server Data Tools
  In questa attività si crea un progetto SSIS mediante **SQL Server Data Tools** per automatizzare la pulizia e corrispondenza dei dati fornitore.  
  
1.  Avviare **SQL Server Data Tools**. Fare clic su Start, scegliere **tutti i programmi**, espandere **Microsoft SQL Server 2012**, fare clic su **SQL Server Data Tools**.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Espandere **Business Intelligence** nel **modelli installati** riquadro e selezionare **Integration Services**.  
  
     ![Visual Studio - finestra di dialogo Nuovo progetto](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - finestra di dialogo Nuovo progetto")  
  
4.  Selezionare **progetto di Integration Services** nel **elenco dei tipi di progetto**.  
  
5.  Tipo di **CleanseAndCurateSuppliers** per **Name** e fare clic su **OK**.  
  
6.  Nelle **Esplora soluzioni** finestra, fare doppio clic su **package. dtsx** e selezionare **rinominare**. Se non viene visualizzata **Esplora soluzioni** finestra, fare clic su **View** nella barra dei menu e fare clic su **Esplora**.  
  
     ![Package. dtsx - Menu Rinomina](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "package. dtsx - Menu Rinomina")  
  
7.  Tipo di **Cleanseandcurate** , quindi premere **invio**. Assicurarsi che il **estensione** rimane **dtsx**.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 5: Aggiunta dell'attività Flusso di dati](task-5-adding-data-flow-task.md)  
  
  

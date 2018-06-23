---
title: Impostare i valori dei parametri dopo la distribuzione del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 311f5cd233819b21d687fc002880518e6c37faa8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069418"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Impostazione dei valori di parametri dopo la distribuzione del progetto
  La Distribuzione guidata consente di impostare i valori dei parametri predefiniti quando si distribuisce il progetto nel catalogo. Quando il progetto si trova nel catalogo, è possibile utilizzare Transact-SQL o Esplora oggetti di SQL Server Management Studio (SSMS) per impostare i valori predefiniti del server.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Per impostare i valori predefiniti del server con Esplora oggetti di SSMS:  
  
1.  Selezionare e fare clic con il pulsante destro del mouse sul progetto nel nodo **Integration Services**.  
  
2.  Per aprire la finestra di dialogo **Proprietà progetto** fare clic su **Proprietà** .  
  
3.  Aprire la pagina dei parametri facendo clic su **Parametri** in **Selezione pagina**.  
  
4.  Selezionare il parametro desiderato nell'elenco **Parametri** . Nota: la colonna **Contenitore** consente di distinguere tra i parametri del progetto e i parametri del pacchetto.  
  
5.  Nella colonna **Valore** specificare il valore del parametro predefinito del server desiderato.  
  
 Per impostare valori predefiniti del server con Transact-SQL, usare la stored procedure [catalog.set_object_parameter_value &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Per visualizzare i valori predefiniti del server corrente, eseguire una query nella vista [catalog.object_parameters &#40;database SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Per cancellare un valore predefinito del server, usare la stored procedure [catalog.clear_object_parameter_value &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi di integrazione &#40;SSIS&#41; parametri](integration-services-ssis-package-and-project-parameters.md)  
  
  

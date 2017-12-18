---
title: Advanced Connection Properties | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fa850af1ac88785ce64d848052b1aa299d7d06b0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="advanced-connection-properties"></a>Advanced Connection Properties
  Utilizzare la finestra di dialogo **Advanced Connection Properties** per aggiungere ulteriori parametri di connessione alla stringa di connessione.  
  
 Può trattarsi di qualsiasi parametro di connessione ODBC supportato dall'istanza del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso.  
  
 I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Properties** vengono aggiunti ai parametri selezionati nella finestra di dialogo **Connect to SQL Server** .  
  
 L'ultima istanza di ogni parametro specificato sostituisce eventuali istanze precedenti del parametro stesso. I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Parameters** seguono e sostituiscono i parametri specificati nella finestra di dialogo **SQL Server Connection** . Ad esempio, se nella finestra di dialogo **Connessione SQL Server** si specifica SERVER1 come nome del server e la pagina **Parametri aggiuntivi per la connessione** contiene ;SERVER=SERVER2, la connessione viene stabilita con SERVER2.  
  
 I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Properties** vengono passati come testo normale.  
  
> [!IMPORTANT]  
>  Non includere le credenziali di accesso nella finestra di dialogo **Advanced Connection Properties** , non verranno crittografate quando vengono passate in rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere a CDC Designer Console](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [Connessione di SQL Server per la creazione dell'istanza](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  

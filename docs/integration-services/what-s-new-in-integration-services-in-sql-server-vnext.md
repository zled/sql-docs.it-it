---
title: "Novit&#224; di Integration Services in SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 3
---
# Novit&#224; di Integration Services in SQL Server vNext
Questo argomento descrive le funzionalità che sono state aggiunte o aggiornate in [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE] SQL Server vNext include anche le funzionalità di SQL Server 2016 e quelle introdotte negli aggiornamenti di SQL Server 2016. Per informazioni sulle nuove funzionalità di SSIS in SQL Server 2016, vedere [Novità di Integration Services in SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="new-in-ssis-in-sql-server-vnext-ctp-11"></a>Novità di SSIS in SQL Server vNext CTP 1.1

In SQL Server vNext CTP 1.1 non sono presenti nuove funzionalità di SSIS.

## <a name="new-in-ssis-in-sql-server-vnext-ctp-10"></a>Novità di SSIS in SQL Server vNext CTP 1.0

### <a name="scale-out-for-ssis"></a>Scalabilità orizzontale per SSIS

La funzionalità di scalabilità orizzontale semplifica l'esecuzione di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] su più computer. 
   
Dopo l'installazione del master e dei ruoli di lavoro di scalabilità orizzontale, il pacchetto può essere distribuito per l'esecuzione automatica in diversi ruoli di lavoro. Se l'esecuzione viene terminata in modo imprevisto, viene ritentata automaticamente. Inoltre, tutte le esecuzioni e i ruoli di lavoro possono essere gestiti centralmente tramite Master.
   
Per altre informazioni, vedere [Scalabilità orizzontale di Integration Services](../integration-services/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Supporto per le risorse di Microsoft Dynamics Online

L'origine OData e la gestione connessione OData supportano ora la connessione ai feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online.

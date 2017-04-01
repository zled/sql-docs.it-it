---
title: "Installazione dei componenti R senza accesso a Internet | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 21
---
# Installazione dei componenti R senza accesso a Internet
  L'installazione dei componenti R usati da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] richiede una connessione Internet per l'accesso ai file disponibili nell'Area download Microsoft o in un altro sito attendibile. Tuttavia, è possibile installare questi componenti in un server senza accesso a Internet, eseguendo copie locali come descritto in questo argomento.  
  
  > [!TIP]
  > 
  > Per una procedura dettagliata del processo di installazione offline, vedere il blog del [team di consulenza clienti di SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)
  
## <a name="installation-on-computers-with-no-internet-access"></a>Installazione in computer senza accesso a Internet  
 Se si esegue un'installazione offline, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] non può accedere ai collegamenti per l'installazione dei componenti R necessari. Per evitare questo problema, è possibile scaricare una copia dei programmi di installazione in locale e completare l'installazione come descritto di seguito.
 
 Si noti che sono disponibili due programmi di installazione per i componenti R, rispettivamente per Microsoft R Open e Microsoft R Server. È necessario scaricare e installare entrambi per l'uso di SQL Server R Services. L'Installazione guidata di SQL Server garantisce che i programmi siano installati nell'ordine corretto.


Versione  |Collegamento di download  
---------|---------
**SQL Server 2016 RTM**     |           
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)     
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)      
**SQL Server 2016 CU 1**     |           
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)     
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)      
**SQL Server 2016 CU 2**     |           
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)     
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)  
**SQL Server 2016 CU 3**     |           
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab: ](https://go.microsoft.com/fwlink/?LinkId=831785)     
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |           
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)     
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)  
**SQL Server 2016 SP 1 GDR**     |           
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)     
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)  

  
**Come aggiornare i componenti R in un'installazione offline**     

1. Usare i collegamenti elencati in precedenza per scaricare la versione appropriata.
2. Copiare i file con estensione cab in una cartella nel computer in cui verrà installato l'aggiornamento.
3. Quando si esegue l'Installazione guidata di SQL Server, fare clic su **Accetto** nella pagina relativa alla licenza di Microsoft R.  Verrà visualizzata una finestra di dialogo in cui sono elencati i collegamenti ai download. Immettere il percorso dei file scaricati. 
4. Fare clic su **Avanti** per indicare che i componenti sono disponibili e completare l'Installazione guidata di SQL Server.
5. Facoltativamente, è anche possibile scaricare il codice sorgente archiviato per i componenti open source. Per altre informazioni, vedere [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).


> [!IMPORTANT] Se si scaricano i file con estensione cab durante l'installazione di SQL Server in un computer con accesso a Internet, l'Installazione guidata rileva la lingua locale e imposta automaticamente la lingua del programma di installazione. 
> 
> Tuttavia, se si installa una delle versioni localizzate di SQL Server in un computer senza accesso a Internet e si scaricano i programmi di installazione di R in una condivisione locale, è necessario modificare manualmente il nome dei file scaricati e inserire l'identificatore di lingua corretto per la lingua di installazione. 
> 
> Ad esempio, se si installa la versione giapponese di SQL Server, si deve modificare il nome del file da SRS_8.0.3.0_1033.cab a SRS_8.0.3.0_1041.cab.    
 
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Risoluzione dei problemi di installazione di R Services](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  
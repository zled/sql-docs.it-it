---
title: Analisi utilizzo software per SQL Server Data Tools | Microsoft Docs
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baf3a205-a6bb-4564-8b64-3a0475bb9273
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7abf9d52d0e8fa4a4c6b16e479891db5f7e95529
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="customer-experience-improvement-program-for-sql-server-data-tools"></a>Analisi utilizzo software per SQL Server Data Tools
  Informazioni su come il programma Analisi utilizzo software consente a Microsoft di identificare modi per migliorare il software.  È possibile configurare gli strumenti per i quali si vuole o meno partecipare in qualsiasi momento.  
  
> [!NOTE]  
>  Per una spiegazione delle procedure di raccolta e di trattamento dei dati per le versioni di Microsoft SQL Server 2016 e qualsiasi altro prodotto o servizio, fare riferimento a questa [informativa sulla privacy da Microsoft](https://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).  
  
## <a name="opting-in-and-out-of-ceip-for-sql-server-data-tools"></a>Consenso o rifiuto esplicito per la partecipazione ad Analisi utilizzo software per SQL Server Data Tools  
 Il programma Analisi utilizzo software è progettato per consentire a Microsoft di migliorare i propri prodotti nel tempo. Questo programma raccoglie informazioni sull'hardware del computer e la modalità di utilizzo del prodotto, senza interrompere gli utenti durante le attività nel computer. Le informazioni raccolte consentono a Microsoft di identificare le funzionalità da migliorare. Questo documento illustra le procedure per acconsentire in modo esplicito alla partecipazione (o rifiutarla in modo esplicito) al programma Analisi utilizzo software per SQL Server Data Tools (SSDT) sia per Visual Studio 2015 che per Visual Studio 2013.  
  
### <a name="choice-and-control-over--ceip-and-sql-server-data-tools-for-visual-studio-2015"></a>Scelta e controllo per il programma Analisi utilizzo software e SQL Server Data Tools per Visual Studio 2015  
 SSDT per Visual Studio 2015 è lo strumento di modellazione dei dati fornito con SQL Server 2016. Questo strumento usa le opzioni di Analisi utilizzo software integrate in Visual Studio 2015. In questo [documento della Guida da Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517102)sono disponibili altre informazioni sull'invio di commenti e suggerimenti tramite Analisi utilizzo software in Visual Studio 2015.  
  
 Nelle versioni di anteprima di SQL Server 2016, la funzionalità Analisi utilizzo software è attivata per impostazione predefinita. È possibile disattivarla o riattivarla seguendo le istruzioni seguenti.  
  
 **In Visual Studio (si applica alle installazioni complete di Visual Studio 2015)**  
  
 Se si esegue l'installazione di SSDT in un computer che dispone già di Visual Studio, vengono aggiunti solo i modelli di progetto Business Intelligence e SQL Server. In questo scenario, le opzioni per l'invio di commenti e suggerimenti offerte da Visual Studio possono essere usare per il consenso o il rifiuto esplicito per Analisi utilizzo software.  
  
1.  Avviare Visual Studio.  
  
2.  Dal menu Guida, selezionare **Invia commenti e suggerimenti** > **Impostazioni**.  
  
3.  Per disattivare Analisi utilizzo software, fare clic su **No, non desidero partecipare**, quindi fare clic su **OK**.  
  
     Per attivare Analisi utilizzo software, fare clic su **Sì, desidero partecipare al programma**, quindi fare clic su **OK**.  
  

  
 **Usare criteri basati sul Registro di sistema o Criteri di gruppo**  
  
 Se si esegue l'installazione di SSDT in un computer che non dispone di Visual Studio 2015, verrà installato solo Visual Studio Shell. La shell non fornisce opzioni per i suggerimenti dei clienti. In questo caso, un aggiornamento del Registro di sistema è l'unica opzione per la configurazione di Analisi utilizzo software.  
  
 I clienti aziendali possono creare Criteri di gruppo per partecipare o meno, impostando criteri basati sul Registro di sistema per SQL Server 2016.  
  
 Le relative impostazioni e chiavi del Registro di sistema sono le seguenti:  
  
 Chiave = HKEY_CURRENT_USER\Software\Microsoft\VSCommon\14.0\SQM  
  
 Nome RegEntry = OptIn  
  
 Tipo voce DWORD:  
  
-   0 è rifiutare esplicitamente  
  
-   1 è acconsentire esplicitamente  
  
> [!CAUTION]  
>  Se il Registro di sistema viene modificato in modo non appropriato, il sistema potrebbe venire gravemente danneggiato. Prima di modificare il Registro di sistema, è consigliabile eseguire il backup di tutti i dati importanti disponibili nel computer. Se si riscontrano problemi dopo l'applicazione di modifiche manuali, è inoltre possibile utilizzare l'opzione di avvio Ultima configurazione valida nota.  
  
 Per altre informazioni sui dati raccolti, elaborati o trasmessi tramite Analisi utilizzo software, vedere l' [Informativa sulla privacy per Analisi utilizzo software Microsoft](http://go.microsoft.com/fwlink/?LinkId=52143).  
  
### <a name="choice-and-control-for-ceip-and-sql-server-data-tools---bi-ssdt-bi"></a>Scelta e controllo per il programma Analisi utilizzo software e SQL Server Data Tools - BI (SSDT-BI)  
 Se si usa SSDT-BI, l'utente potrà scegliere di partecipare ad Analisi utilizzo software durante l'installazione. In seguito, le modifiche alla configurazione di Analisi utilizzo software per SSDT-BI possono essere apportate mediante gli strumenti client o modificando le impostazioni del Registro di sistema.  
  
 **In SSDT e SSDT-BI per Visual studio 2013**  
  
1.  Avviare lo strumento e aprire un progetto nuovo o esistente di Analysis Services o Integration Services.  
  
2.  Scegliere **Opzioni commenti e suggerimenti utenti di Microsoft SQL Server**dal menu ?.  
  
3.  Per disattivare Analisi utilizzo software, fare clic su **No, non desidero partecipare**.  
  
     Per attivare Analisi utilizzo software, fare clic su **Sì, desidero partecipare**.  
  
4.  Scegliere **OK**.  
  
 **Usare criteri basati sul Registro di sistema o Criteri di gruppo**  
  
 I clienti aziendali possono creare Criteri di gruppo per partecipare o meno impostando criteri basati sul Registro di sistema per SQL Server 2014.  
  
 Le relative impostazioni e chiavi del Registro di sistema sono le seguenti:  
  
 Chiave = HKEY_CURRENT_USER\Software\Microsoft\Microsoft SQL Server\120  
  
 Nome RegEntry = CustomerFeedback  
  
 Tipo voce DWORD:  
  
-   0 è rifiutare esplicitamente  
  
-   1 è acconsentire esplicitamente  
  
  


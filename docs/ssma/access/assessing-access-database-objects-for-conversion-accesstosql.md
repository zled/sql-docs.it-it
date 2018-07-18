---
title: Valutazione di accedere agli oggetti di Database per la conversione (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d2d804734432cfd396acb017d6358310debeec1f
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979423"
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>Valutazione di accedere agli oggetti di Database per la conversione (AccessToSQL)
Prima di caricare gli oggetti e la migrazione dei dati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario determinare quanto la migrazione avrà esito positivo, e quanto tempo potrebbe richiedere la conversione. SSMA è possibile creare un report di valutazione che mostra la percentuale di oggetti che sono state convertite correttamente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi di SQL Azure e l'ora le stime per eseguire la migrazione. SSMA consente inoltre di visualizzare i problemi specifici che generava errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Durante la creazione di un report di valutazione, SSMA converte gli oggetti di database di Access selezionati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi di SQL Azure e quindi Mostra i risultati.  
  
**Per creare un report di valutazione**  
  
1.  Nel Visualizzatore metadati di accesso, selezionare uno o più database che si desidera valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto agli oggetti che non si desidera valutare.  
  
3.  Fare doppio clic su **database**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti facendo clic su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA Mostra lo stato di avanzamento nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si noteranno anche messaggi nel riquadro di Output.  
  
Una volta completata, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Access: viene visualizzata la finestra di Report di valutazione.  
  
## <a name="using-assessment-reports"></a>Uso dei report di valutazione  
Nella finestra di Report di valutazione sono contenuti tre riquadri: uno strumento di esplorazione, un riquadro dei dettagli e un riquadro del messaggio.  
  
-   Il riquadro di explorer consente di esplorare gli oggetti che sono stati valutati. È possibile fare clic sugli elementi in questo riquadro per eseguire il drill-down delle chiavi, indici e le singole tabelle.  
  
-   Il riquadro dei dettagli Mostra le statistiche di conversione per l'oggetto selezionato.  
  
-   Viene illustrato il riquadro del messaggio di errori, avvisi e messaggi informativi per la conversione e ora le stime per eseguire la migrazione e i passaggi di correzione degli errori.  
  
È necessario correggere gli errori prima di eseguire di nuovo il report di valutazione o convertire gli schemi. Per trovare gli errori, scegliere il **errori** pulsante nel riquadro dei messaggi e quindi espandere ogni errore per visualizzare un elenco di oggetti in cui si è verificato l'errore. Se si fa clic su un oggetto nel riquadro dei messaggi, tutti gli errori e avvisi per l'oggetto verranno visualizzato nel riquadro dei dettagli.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di oggetti di database di Access](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  

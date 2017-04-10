---
title: "Lezione 8: Creare indicatori di prestazioni chiave | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 8: Creare indicatori di prestazioni chiave
In questa lezione verranno creati indicatori di prestazioni chiave (KPI). Gli indicatori di prestazioni chiave vengono usati per misurare le prestazioni di un valore, definito mediante una misura di *base*, rispetto a un valore *target*, definito anch'esso da una misura o da un valore assoluto. Nelle applicazioni client di creazione di report, gli indicatori KPI possono fornire ai professionisti aziendali un metodo semplice e veloce per comprendere l'andamento aziendale in generale o per identificare le tendenze. Per altre informazioni, vedere [KPI &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 7: Creare misure](../analysis-services/lesson-7-create-measures.md).  
  
## Creare indicatori di prestazioni chiave  
  
#### Per creare un indicatore KPI relativo alle prestazioni delle vendite Internet trimestrali correnti  
  
1.  In Progettazione modelli fare clic sulla tabella (scheda) **Internet Sales**.  
  
2.  Nella griglia delle misure fare clic su una cella vuota.  
  
3.  Sulla barra della formula sopra la tabella digitare la formula seguente:  
  
    **Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
    Tale misura definirà fungerà da misura di base per l'indicatore KPI.  
  
4.  Nella griglia delle misure fare clic con il pulsante destro del mouse sulla misura **Internet Current Quarter Sales Performance**, quindi scegliere **Crea KPI**.  
  
    Verrà visualizzata la finestra di dialogo **Indicatore di prestazioni chiave**.  
  
5.  Nella finestra di dialogo **Indicatore di prestazioni chiave (KPI)** selezionare l'opzione **Valore assoluto** in **Destinazione**.  
  
6.  Nel campo **Valore assoluto** digitare **1.1**, quindi premere INVIO.  
  
7.  Nel campo relativo al dispositivo di scorrimento sinistro (in basso) digitare **1**, quindi nel campo relativo al dispositivo di scorrimento destro (in alto), digitare **1.07**.  
  
8.  In **Seleziona stile icona** selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde).  
  
    > [!TIP]  
    > Si noti il campo espandibile **Descrizioni** sotto gli stili di icona disponibili. È possibile digitare le descrizioni per i diversi elementi KPI per semplificarne l'identificazione nelle applicazioni client.  
  
9. Fare clic su **OK** per completare l'indicatore KPI.  
  
    Nella griglia delle misure osservare l'icona accanto alla misura **Internet Current Quarter Sales Performance**. Questa icona indica che la misura funge da valore di base per un indicatore KPI.  
  
#### Per creare un indicatore KPI relativo alle prestazioni dei margini Internet trimestrali correnti  
  
1.  Nella griglia delle misure per la tabella **Internet Sales** fare clic su una cella vuota.  
  
2.  Sulla barra della formula sopra la tabella digitare la formula seguente:  
  
    **Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
3.  Nella griglia delle misure fare clic con il pulsante destro del mouse sulla misura **Internet Current Quarter Margin Performance**, quindi scegliere **Crea KPI**.  
  
4.  Nella finestra di dialogo **Indicatore di prestazioni chiave** selezionare l'opzione **Valore assoluto** in **Definisci valore di destinazione**.  
  
5.  Nel campo **Valore assoluto** digitare **1.25**.  
  
6.  In **Definisci soglie stato** far scorrere il dispositivo di scorrimento sinistro (in basso) fino a quando non viene visualizzato **0.8**, quindi far scorrere il dispositivo di scorrimento destro (in alto) fino a quando non viene visualizzato **1.03**.  
  
7.  In **Seleziona stile icona** selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde), quindi fare clic su **OK**.  
  
## Passaggio successivo  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 9: Creare prospettive](../Topic/Lesson%209:%20Create%20Perspectives.md).  
  
  
  

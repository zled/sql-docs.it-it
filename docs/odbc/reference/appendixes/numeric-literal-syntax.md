---
title: Sintassi del valore letterale numerica | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a371ac49fe29674a1e9c0d7bb0dd9639ba5aa48
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="numeric-literal-syntax"></a>Sintassi del valore letterale numerica
Per i valori letterali numerici in ODBC, viene utilizzata la sintassi seguente:  
  
 *valore letterale numerico* :: = *letterale numeric firmati &#124; letterale numerico senza segno*  
  
 *literal numeric firmati* :: = [*sign*] *letterale numerico senza segno*  
  
 *letterale numerico senza segno* :: = *letterale numerico esatto &#124; letterale numerici approssimati*  
  
 *letterale numerico esatto* :: = *intero senza segno* [*periodo*[*intero senza segno*]] *&#124; periodo di unsigned integer*  
  
 *accesso* :: = *segno &#124; meno (-)*  
  
 *literal numerici approssimati* :: = *esponente mantissa E*  
  
 *mantissa* :: = *letterale numerico esatto*  
  
 *esponente* :: = *integer firmato*  
  
 *integer firmato* :: = [*sign*] *intero senza segno*  
  
 *intero senza segno* :: = *cifre...*  
  
 *segno* :: =*+*  
  
 *segno di sottrazione* :: = -  
  
 *cifra* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 6 5 &#124; &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *periodo* :: =.

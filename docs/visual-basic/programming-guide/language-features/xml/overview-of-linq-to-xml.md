---
title: Vue d'ensemble de LINQ to XML dans Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 65df48112834be04dc8d3b62b8b163316b06c4a6
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753407"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Vue d'ensemble de LINQ to XML dans Visual Basic
Visual Basic prend en charge [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] via des littéraux XML et les propriétés d’axe XML. Cela vous permet d’utiliser une syntaxe familière et pratique pour l’utilisation de code XML dans votre code Visual Basic. *Littéraux XML* vous permettent d’inclure du XML directement dans votre code. *Propriétés d’axe XML* vous permettent d’accéder aux nœuds enfants, nœuds descendants et attributs d’un littéral XML. Pour plus d’informations, consultez [vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) et [l’accès à un XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est conçu spécifiquement pour tirer parti des API de programmation XML en mémoire [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Bien que vous puissiez appeler les [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API directement, seul Visual Basic vous permet de déclarer des littéraux XML et accéder directement aux propriétés d’axe XML.  
  
> [!NOTE]
>  Littéraux XML et les propriétés d’axe XML ne sont pas pris en charge dans le code déclaratif dans une page ASP.NET. Pour utiliser les fonctionnalités XML de Visual Basic, placez votre code dans une page code-behind dans votre application ASP.NET.  
  
 ![lien vers la vidéo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") pour des démonstrations vidéo connexes, consultez [How Do I Get Started with LINQ to XML ?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) et [comment faire pour créer des feuilles de calcul Excel à l’aide de LINQ to XML ?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).  
  
## <a name="creating-xml"></a>Création de XML  
 Il existe deux façons de créer des arborescences XML en Visual Basic. Vous pouvez déclarer un littéral XML directement dans le code, ou vous pouvez utiliser la [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API pour créer l’arborescence. Les deux processus permettent au code afin de refléter la structure finale de l’arborescence XML. Par exemple, l’exemple de code suivant crée un élément XML :  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Pour plus d’informations, consultez [création de XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Accès et navigation dans XML  
 Visual Basic fournit des propriétés d’axe XML pour l’accès et la navigation dans les structures XML. Ces propriétés permettent d’accéder aux éléments et attributs XML en spécifiant les noms des éléments enfants XML. Ou bien, vous pouvez appeler explicitement la [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] méthodes de navigation et recherche d’éléments et attributs. Par exemple, l’exemple de code suivant utilise les propriétés d’axe XML pour faire référence aux attributs et éléments enfants d’un élément XML. L’exemple de code utilise un [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête pour récupérer des éléments enfants et les sortir comme éléments XML, en effectuant efficacement une transformation.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Pour plus d’informations, consultez [l’accès à un XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Visual Basic vous permet de spécifier un alias pour un espace de noms XML global en utilisant la `Imports` instruction. L’exemple suivant montre comment utiliser la `Imports` instruction pour importer un espace de noms XML :  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Vous pouvez utiliser un alias d’espace de noms XML lorsque vous accéder aux propriétés d’axe XML et déclarez des littéraux XML pour les documents XML et des éléments.  
  
 Vous pouvez récupérer un <xref:System.Xml.Linq.XNamespace> objet pour un préfixe d’espace de noms particulier à l’aide de la [opérateur GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Pour plus d’informations, consultez [Imports, instruction (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>À l’aide des espaces de noms XML dans les littéraux XML  
 L’exemple suivant montre comment créer un <xref:System.Xml.Linq.XElement> objet qui utilise l’espace de noms global `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 Le compilateur Visual Basic convertit des littéraux XML qui contiennent des alias d’espace de noms XML en code équivalent, qui utilise la notation XML pour l’utilisation d’espaces de noms XML, avec la `xmlns` attribut. Lors de la compilation, le code dans l’exemple précédent produit essentiellement le même code exécutable comme l’exemple suivant :  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>À l’aide des espaces de noms XML dans les propriétés d’axe XML  
 Espaces de noms XML déclarés dans les littéraux XML ne sont pas disponibles pour une utilisation dans les propriétés d’axe XML. Toutefois, espaces de noms globaux peut être utilisé avec les propriétés d’axe XML. Utilisez un signe deux-points pour séparer le préfixe d’espace de noms XML à partir du nom de l’élément local. Voici un exemple :  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)

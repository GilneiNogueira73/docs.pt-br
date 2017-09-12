---
title: Exemplo de tecnologia de SchemaImporterExtension
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: be04c759d53b74208ac4e9a9cf7a2ac4cf3f8cce
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="15992-102">Exemplo de tecnologia de SchemaImporterExtension</span><span class="sxs-lookup"><span data-stu-id="15992-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="15992-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="15992-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="15992-104">Esse exemplo demonstra um <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> personalizado que permite um controle fino sobre a geração de código quando um esquema XML é importado.</span><span class="sxs-lookup"><span data-stu-id="15992-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="15992-105">O aplicativo mostra como criar, registrar e invocar essa extensão.</span><span class="sxs-lookup"><span data-stu-id="15992-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="15992-106">Para criar o exemplo usando o prompt de comando</span><span class="sxs-lookup"><span data-stu-id="15992-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="15992-107">Abra uma janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="15992-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="15992-108">Digite **msbuild.exe OrderSchemaImporterExtension.sln** na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="15992-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="15992-109">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15992-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="15992-110">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="15992-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="15992-111">Clique duas vezes no ícone para OrderSchemaImporterExtension.sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15992-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="15992-112">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="15992-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="15992-113">O aplicativo será criado no diretório padrão \bin ou \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="15992-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="15992-114">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="15992-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="15992-115">Navegue para o diretório contendo o novo executável, usando o prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="15992-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="15992-116">Digite **[nome do executável]** na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="15992-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15992-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="15992-117">Remarks</span></span>  
 <span data-ttu-id="15992-118">Para obter mais informações sobre a criação do binário de exemplo e as etapas de registro, consulte os comentários no código de origem e nos arquivos build.proj.</span><span class="sxs-lookup"><span data-stu-id="15992-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15992-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15992-119">See Also</span></span>  
 <xref:System.CodeDom.CodeCompileUnit>   
 <xref:System.CodeDom.CodeNamespace>   
 <xref:System.CodeDom.CodeNamespaceImport>   
 <xref:Microsoft.CSharp.CSharpCodeProvider>   
 <xref:System.Xml.Serialization.IXmlSerializable>   
 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>   
 <xref:System.CodeDom>   
 <xref:System.CodeDom.Compiler>   
 <xref:System.Web.Services.Description>   
 <xref:System.Web.Services.Discovery>   
 <xref:System.Xml.Serialization>   
 <xref:System.Uri>   
 <xref:Microsoft.VisualBasic.VBCodeProvider>   
 <xref:System.Web.Services.Description.WebReference>   
 <xref:System.Xml.Serialization.XmlSchemaImporter>

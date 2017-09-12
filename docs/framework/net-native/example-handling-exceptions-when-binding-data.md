---
title: "Exemplo: lidando com exceções ao associar dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aea6051a5cfd436b879bc3c8c6ce9b5f656c0ecb
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="24d2b-102">Exemplo: lidando com exceções ao associar dados</span><span class="sxs-lookup"><span data-stu-id="24d2b-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
>  <span data-ttu-id="24d2b-103">Este tópico refere-se ao Developer Preview do .NET Nativo, que é um software em pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="24d2b-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="24d2b-104">Você pode baixar a versão prévia do [site Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (registro obrigatório).</span><span class="sxs-lookup"><span data-stu-id="24d2b-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="24d2b-105">O exemplo a seguir mostra como resolver uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) gerada quando um aplicativo compilado com a cadeia de ferramentas do [!INCLUDE[net_native](../../../includes/net-native-md.md)] tenta associar dados.</span><span class="sxs-lookup"><span data-stu-id="24d2b-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain tries to bind data.</span></span> <span data-ttu-id="24d2b-106">Aqui estão as informações da exceção:</span><span class="sxs-lookup"><span data-stu-id="24d2b-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="24d2b-107">Esta é a pilha de chamadas associadas:</span><span class="sxs-lookup"><span data-stu-id="24d2b-107">Here's the associated call stack:</span></span>  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="24d2b-108">O que o aplicativo estava fazendo?</span><span class="sxs-lookup"><span data-stu-id="24d2b-108">What was the app doing?</span></span>  
 <span data-ttu-id="24d2b-109">Na base da pilha, os quadros do namespace [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) indicam que o mecanismo de renderização de XAML estava em execução.</span><span class="sxs-lookup"><span data-stu-id="24d2b-109">At the base of the stack, frames from the [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="24d2b-110">O uso do método <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=fullName> indica uma pesquisa de reflexão do valor da propriedade no tipo cujos metadados foi removido.</span><span class="sxs-lookup"><span data-stu-id="24d2b-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=fullName> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="24d2b-111">A primeira etapa no fornecimento de uma diretiva de metadados seria adicionar metadados `serialize` ao tipo de forma que suas propriedades estejam acessíveis:</span><span class="sxs-lookup"><span data-stu-id="24d2b-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="24d2b-112">Esta é uma ocorrência isolada?</span><span class="sxs-lookup"><span data-stu-id="24d2b-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="24d2b-113">Neste cenário, se a associação dos dados possuem metadados incompletos para um `ViewModel`, isso também pode ocorrer para outros.</span><span class="sxs-lookup"><span data-stu-id="24d2b-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="24d2b-114">Se o código é estruturado de forma que os modelos de exibição do aplicativo estão todos no namespace `App.ViewModels`, você pode usar uma diretiva de tempo de execução mais geral:</span><span class="sxs-lookup"><span data-stu-id="24d2b-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="24d2b-115">O código pode ser reconfigurado para não usar reflexão?</span><span class="sxs-lookup"><span data-stu-id="24d2b-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="24d2b-116">Como associação de dados possui reflexão intensa, alterar o código para evitar reflexão não é viável.</span><span class="sxs-lookup"><span data-stu-id="24d2b-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="24d2b-117">No entanto, existem maneiras para especificar o `ViewModel` para a página XAML para que a cadeia de ferramentas possa associar propriedades de vinculação com o tipo correto no tempo de compilação e manter os metadados sem usar uma diretiva de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="24d2b-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="24d2b-118">Por exemplo, você pode aplicar o [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) atributo a propriedades.</span><span class="sxs-lookup"><span data-stu-id="24d2b-118">For example, you could apply the [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) attribute on properties.</span></span> <span data-ttu-id="24d2b-119">Isso faz com que o compilador XAML gere informações de pesquisa necessárias e evita que necessitem de uma diretiva de tempo de execução no arquivo Default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="24d2b-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d2b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24d2b-120">See Also</span></span>  
 <span data-ttu-id="24d2b-121">[Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md) </span><span class="sxs-lookup"><span data-stu-id="24d2b-121">[Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) </span></span>  
 [<span data-ttu-id="24d2b-122">Exemplo: solução de problemas de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="24d2b-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
